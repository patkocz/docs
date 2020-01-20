# Docker

## Docker images

Download docker image from docker hub

```
docker pull <image_name>:version    # default is lates
docker pull alpine
```

Show downloaded images

```
docker images
```

Delete downloaded images

```
docker rmi <image_id>
docker rmi baa5d63471ea

docker rmi $(docker images -q)  # remove all images
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

docker diff shows the difference between file in container and image

```
Docker diff <container_name>|<container_id>
```

To show logs from container run

```
docker logs -f <container_name>|<container_id>
```

## Docker volumes

## Docker networks

## Docker compose
