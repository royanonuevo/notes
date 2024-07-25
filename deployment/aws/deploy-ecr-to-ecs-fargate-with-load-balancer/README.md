# CI/CD for AWS ECR, ECS Fargate with Load Balancer 

## 1. Create 2 Security Groups
1. **ALB-SG** Inbound Rules: 
   - `HTTP`, `80`, `Anywhere-IPv4` 
   - `HTTP`, `80`, `Anywhere-IPv6`
   - `HTTP`, `3000`, `Anywhere-IPv4`
   - `HTTP`, `3000`, `Anywhere-IPv6`
2. **ECS-SG** Inbound Rules: 
   - `All Traffic`, `All`, Custom: `ALB-SG` (Select the 1st SG your created)

## 2. Create Target Group
Under `EC2` > **Load Balancing** (Sidebar) > `Target Groups`
- Target Type: IP addresses
- Target Group Name: Put a name you want ex: nextjs-ecs-tg
- Create `Next` and `Create Target Group`


## 3. Create Load Balancer
Under `EC2` > **Load Balancing** (Sidebar) > `Load Balancers`
- Load balancer types: `Application Load Balancer`
- Load balancer name: Put a name you want ex: next-elb
- Under Mappings, Select all availability zones
- Security Group: Select the existing security group you created for **ALB-SG** 

## 4. ECR and ECS Setup
1. Create **ECR Repository** and upload the docker images
2. Create **ECS Cluster**
   - For Infrastructure, select `AWS Fargate`
3. Create **ECS Task Definition** 
   - For Infrastructure, select `AWS Fargate`
   - Operating system/Architecture: `Linux/X86_64`
   - For Container imageUri copy the imageUri you uploaded from ECR Repository
   - For Port Mapping, Container Port: Put the `NextJS App Port` as a `Container Port` ex: `3000`
4. Create **Service**
   - Under the `ECS Cluster` you created, create `service`
   - Compute options: `Launch Type`
   - Application Type: `Service`
   - Family: Choose the existing `task definition` you created
   - Add `Service Name` you want
   - Under Networking, choose the existing security group you created for **ECS-SG**
   - Under Load Balancer:
      - Load balancer type: `Application Load Balancer`
      - Application Load Balancer: `Use the existing Load Balancer you created`
      - Listener: `Use the existing Listener you created '80:HTTP'`
      - Target group: `Use the existing target group you created `

## 5. Testing
1. AWS has bugs, check the existing security group you created and modify or add again inbound rules if needed
2. Check if all task is in `running` status
3. Check if all registered target in `Target Group` you created is `Healthy`
4. Copy the `DNS name` from your load balancer and test it in your favorite browser.



## 6. Add Github Action
Reference: [https://www.youtube.com/watch?v=wLsWALjM-Uk](https://www.youtube.com/watch?v=wLsWALjM-Uk)
1. Prepare the following variables:
   - ECR_IMAGE_NAME
   - ECS_CLUSTER_NAME
   - ECS_SERVICE_NAME
   - AWS_DEFAULT_REGION
2. Prepare the following secrets:
   - AWS_ACCESS_KEY_ID 
   - AWS_SECRET_ACCESS_KEY
   - AWS_ACCOUNT_ID 
3. `access key id` and `secret key` can able to get from AWS `IAM` > `Users` > `Securiy Credentials`
   - Setup [AWS CLI On Linux Reference](https://www.youtube.com/watch?v=1OqMQPx8Jno)
4. Sample [github yaml file](./.github/workflows/deploy-to-ecs.yaml)

---
## Clean Up Old Images in ECR Using ECR Lifecycle Policies
https://blog.stackademic.com/cleanup-old-images-in-ecr-using-ecr-lifecycle-policies-e7cbf60e9827
