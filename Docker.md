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
```

- List Images
```bash
docker image ls
```

- Run Container
```bash
docker run -d -p {machine port}:{container port} --name {container_name} {image_name}:{tag}
```

- Delete All Unused Images
```bash
docker image prune -a
```

- Delete All Unused Containers
```bash
docker container rm $(docker container ls -aq)
```

### Docker Compose Commands

- Pull Image
```bash
docker compose up
docker compose down
```
