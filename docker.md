# Docker

Docker is an open platform for developing, running and deploying applications inside containers. Docker can run on Windows, MacOS and Linux.

## Docker images

Download docker image from docker hub

```docker
docker pull [OPTIONS] NAME[:TAG|@DIGEST]

# OPTIONS
-a: get all tags
-q: suppress verbose output

# Examples
docker pull alpine
docker pull alpine:latest
docker pull alpine@sha256:3a7fea6c4cf9c25ccf2...

# Pull image from different registry
docker pull myregistry.local:5000/testing/test-image

# Pull all images from registry
docker pull -a alpine
```

To tag your image

```docker
docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]

# Example
docker tag apress/exampleapp:changed adamfreeman/exampleapp:changed
```

push your docker image to docker hub

```docker
docker push [OPTIONS] NAME[:TAG]

# Example
docker push username/my-repo
```

Show downloaded images

```docker
docker images [OPTIONS] [REPOSITORY[:TAG]]

# OPTIONS
-a, --all:    show all images
--format:     Pretty-print images using a Go template
-q, --quiet:  show only ID
```

Delete downloaded images

```docker
docker rmi [OPTIONS] IMAGE [IMAGE...]

# OPTIONA
-f: force removal, even if exists container based on this image

# Example
docker rmi <image_id>
docker rmi baa5d63471ea
docker rmi -f alpine:latest

# remove all images
docker rmi $(docker images -q)
```

## Dockerfile

Dockerfile allow you to create custom image. It contains series of instructions to create new docker image.

```
FROM microsoft/aspnetcore:1.1.1
COPY dist /app
WORKDIR /app
EXPOSE 80/tcp
ENTRYPOINT ["dotnet", "HelloWorld.dll"]
```

to build image from Dockerfile run

```
docker build . -t myapp/helloworld -f Dockerfile
```

## Docker containers

Create container from image

```
docker create -p 3000:80 --name myApp myapp/helloworld
```

To show containers run

```
docker ps       # show running containers
docker ps -a    # show all containers
```

To start container run

```
docker start <container_name>|<container_id>
docker start myApp

docker start $(docker ps -aq)   # start all containers
```

To create and run docker container in one step use

```
docker run
```

To stop running container run

```
docker stop <container_name>|<container_id>
```

To remove contaier run

```
docker rm <container_name>|<container_id>
```

docker diff shows the difference between file in container and image

```
Docker diff <container_name>|<container_id>
```

To show logs from container run

```
docker logs -f <container_name>|<container_id>
```

If You want to run command inside a container run

```
docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
```

## Docker volumes

## Docker networks

## Docker compose
