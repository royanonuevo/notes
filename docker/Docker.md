# Docker 

This is a sheetcheat/ tips on how to use Docker to create and manage containers

## Prerequisites

- Install [Docker](https://www.docker.com/products/docker-desktop/) for database containerization.
- Basic Knowledge of Linux commands

### Docker Commands in Dockerfile

- `FROM`: Base Image to build on top of it.
- `WORKDIR`: Set the working directory. 
- `COPY`: Copy files from the host to the container.
- `RUN`: Execute a command in the container.
- `EXPOSE`: Expose a port to the host. 
- `ENV`: Set environment variables.
- `ARG`: Set build-time variables.
- `VOLUME`: Create a mount point.
- `CMD`: Execute a command when the container starts.
- `ENTRYPOINT`: Execute a command when the container starts, and it cannot be overridden.

### Docker Commands in Docker CLI

- Pull Image
```bash
docker pull {image_name}:{tag} 
```

- Build Image
```bash
docker build -t {image_name}:{tag} .
docker build -f Dockerfile.dev -t {image_name}:{tag} .
docker build --platform linux/amd64 -t anonuevoroy/my-ui-library .
```

- List Images
```bash
docker image ls
```

- Run Container
```bash
docker run -d -p {machine port}:{container port} --name {container_name} {image_name}:{tag}
```

- Delete All Images
```bash
docker rmi -f $(docker images -aq)
```

- Delete Containers
```bash
docker container rm $(docker container ls -aq) // Delete All Unused Containers
docker stop $(docker ps -a -q) // Stop all the containers
docker rm $(docker ps -a -q) // Remove all the containers
```

### Docker Compose Commands
```bash
docker compose up
docker compose up client-dev
docker compose up client-prod

docker compose down

```
