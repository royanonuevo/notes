# How to Deploy and Setup CI/CD

1. Setup VPS server or launch new ec2 instance (ubuntu)
    - Generate and Add SSH
    - Access the server via SSH
2. Install `docker` in the server using **setup-docker.sh**
    - Create `scripts` and `docker` folder
    - cd inside `scripts`
    - Create and run [setup-docker.sh](./ubuntu/docker/setup-docker.md)

3. install `nginx` in the server using **setup-nginx.sh**
    - Inside "scripts" folder 
    - Create and run [setup-nginx.sh](./ubuntu/nginx/setup-nginx.md)
4. (If you want to try to skip ci/cd and directly deploy the application) Pull the docker image in the server and run the image container

___

## Add Github Action
1. In your github repository `settings > Secrets and variables > Actions > Secrets Tab > Repository secrets`, provide the following secrets:
    - DOCKERHUB_USERNAME
    - DOCKERHUB_TOKEN
    - SSH_HOST
    - SSH_USER
    - SSH_PRIVATE_KEY

2. Create new file and folder in your root project: `.github/workflows/deploy.yaml`
3. create a new file in your root project, and add `docker/docker-compose.yaml` file
4. create a new file in your root project, and add `scripts/deploy.sh` file
    
