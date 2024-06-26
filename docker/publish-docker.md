# Publish Docker Image


## Prerequisites

- Login to Docker Hub and create new repository
- Make sure to use Access Token from docker hub to authenticate in your local


### Docker Commands 

#1. Login
```bash
docker login
```


#2. Build the Image, make sure that the name is same with the repository name in docker hub
```bash
docker build -t {image_name}:{tag} .
docker build -f Dockerfile.dev -t {image_name}:{tag} .
docker build -f Dockerfile.dev -t anonuevoroy/my-ui-library .
docker build --platform linux/amd64 -f Dockerfile.dev -t anonuevoroy/my-ui-library .
```

#3. Push Image in Docker Hub
```bash
docker push {dockerhub username}/{image_name}
```
