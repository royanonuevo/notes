# How to Deploy and setup CI/CD

1. Setup VPS server or launch new ec2 instance (ubuntu)
    - Generate and Add SSH
    - Access the server via SSH
2. Install `docker` in the server using **setup-docker.sh**
    - Make `scripts` directory
    - Create and run [setup-docker.sh](./ubuntu/docker/setup-docker.md)

3. install `nginx` in the server using **setup-nginx.sh**
    - Inside "scripts" folder 
    - Create and run [setup-nginx.sh](./ubuntu/nginx/setup-nginx.md)
4. (If you want to try to skip ci/cd and directly deploy the application) Pull the docker image in the server and run the image container

---
---

1. dockerize the app
2. add github action
    