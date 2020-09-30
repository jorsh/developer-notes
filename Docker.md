# Docker

Docker is a platform for developers and sysadmins to develop, deploy, and run applications with containers.

Containerization is increasingly popular because containers are:

- Flexible: Even the most complex applications can be containerized.
- Lightweight: Containers leverage and share the host kernel.
- Interchangeable: You can deploy updates and upgrades on-the-fly.
- Portable: You can build locally, deploy to the cloud, and run anywhere.
- Scalable: You can increase and automatically distribute container replicas.
- Stackable: You can stack services vertically and on-the-fly.

## Docker Benefits

- Accelerate developer onboarding
- Eliminate app conflicts
- Environment consistency
- Ship softare faster

# Dis

Containers don't run at bare-metal speeds.
Persistent data storage is complicated.
Not all applications benefit from containers.
Increased complexity due to an additional layer.
Managing a huge amount of containers is challenging

## List Docker CLI commands

```
docker
docker container --help

## Display Docker version and info
docker --version
docker version
docker info

## Key Docker Client Commands
docker pull <image-name>
docker run <image-name>
docker image ls
docker rmi <image-name>

## List Docker containers (running, all, all in quiet mode)
docker container ls
docker container ls --all
docker container ls -aq
docker ps
docker rm <container-id>
```
