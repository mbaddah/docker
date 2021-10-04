


```docker

### list containers
docker ps

### starting a container
docker start x

### stopping a container
docker stop x

### running a container
docker run x
docker run -d x // -d run in background

### running a container with interactive shell. Standard in
docker run -it busybox sh

### exec - execute command inside container running
e.g. 
docker exec -it containerid sh

### prune all containers
docker container prune

### build docker image
docker build .

### Inside Dockerfile

#### 1. Select base image - FROM
FROM alpine

#### 2. Download dependencies - RUN
RUN apk add --update redis
RUN apk add --update gcc


#### 3. Start command - CMD
CMD ["redis-server"]

### COPY
COPY from (build context) to (destination in container)

### -t tag
dockername/nameofimage

### -p port mapping
-p (route incoming request to this port on local host to) : (port inside container)

docker run -p 8080:8080 imagename


### WORKDIR - working dir
Any following command will be executed relative to this path in container



### Docker-compose
- Used to start multiple docker containers
- automate process
- yaml format:

version: version of docker compose

services: type  of container
    name-of-service:
        imgae: 'name of image'
    name-of-service:
        build: .
        ports:
            - "x:y"


docker run myimage = docker-compose up

docker build . / docker run myimage = docker-compose up --build

docker-compose up -d # start all containers in background

docker-compose down # bring down all running containers

### restart policies
- no : default.
- always
- on-failure
- unless-stopped

### customer docker file
docker build -f customerfilename .

docker-compose ps # list containers running via docker-compose. Must be run in same dir as docker-compose.yml

### Setting up volumes

docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <image_id>

Notes:

* The ':' colon symbol maps folder inside container to folder outside container
* -v /app/node_modules create placeholder because we don't have node_modules directory in host directory (this gets created inside the container at runtime)


```


