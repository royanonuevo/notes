# Deploy AWS ECR to ECS Fargate
1. Create **ECR Repository** and upload the docker images on that
2. Create **ECS Cluster**
   - For Infrastructure, select `AWS Fargate`
3. Create **ECS Task Definition** 
   - For Infrastructure, select `AWS Fargate`
   - Operating system/Architecture: `Linux/X86_64`
   - For Container imageUri copy the imageUri you uploaded from ECR Repository
   - For Port Mapping, Container Port: Put the `NextJS App Port` as a `Container Port`
4. Create **Service**
   - Under the `ECS Cluster` you created, create `service`
   - Compute options: `Launch Type`
   - Application Type: `Service`
   - Family: Choose the task definition you created
   - Add Service Name you want
   - Under Networking, choose a security Group with the port same with your `NextJS App Port` as a `Container Port` or Create New:
      - Type: Custom TCP
      - Port: same with your `NextJS App Port` as a `Container Port`
      - Source: Anywhere
5. Copy the `public ip` address and test it in the browser
__
## Add Load Balancer
1. Create New `Load Balancer` > Select `Application Load Balancer`
2. Select `Internet-facing`
3. Under Network Mapping, select all available
4. Under Security Group: Select with 80 port
5. Under `Listeners and routing`, Protocol: HTTP Port: 80
   1. Create Target Group
   2. Target Type: IP addresses
   3. Paste the Private Network with a port of `NextJS App Port` as a `Container Port`
   4. Make sure to click the `Include as pending below` button
6. Copy the `DNS name` and test
__
## Add Github Action
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
access key id and secret key can able to get from AWS `IAM` > `Users` > `Securiy Credentials`
   - Setup [AWS CLI On Linux Reference](https://www.youtube.com/watch?v=1OqMQPx8Jno)

