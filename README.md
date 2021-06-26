# docker-example

## Commands

### Hello World
    docker images
    docker run busybox:1.33.1 echo "hello world"
    docker run busybox:1.33.1 ls /
    docker run -it busybox:1.33.1
        1. ls
        2. touch a.txt
        3. ls
        4. exit
    docker run -it busybox:1.33.1
        1. ls
        2. exit
    docker rmi image_id

### Basic Commands
    docker ps
    docker ps -a
    docker run -d busybox:1.33.1 sleep 1000
    docker inspect container_id
    docker stop container_id
    docker rm container_id
    docker rm $(docker ps -a -q)
    docker run --rm busybox:1.33.1 sleep 10    

### Port Mapping and Logs
    docker run -it -p 8888:8080 tomcat:8.0
    docker run -it -d -p 8888:8080 tomcat:8.0
    docker ps -a
    docker logs container_id

### Build Docker Images with Dockerfile
    nano Dockerfile
        FROM debian:jessie
        RUN apt-get update 
        RUN apt-get install -y htop
    docker build -t afonsobarrenha/debian:1.0.0 . 
    docker images 
    docker run -it afonsobarrenha/debian:1.0.0

    nano Dockerfile
        FROM debian:jessie
        RUN apt-get update 
        RUN apt-get install -y htop
        CMD ["htop"]
    docker build -t afonsobarrenha/debian:1.1.0 . 

    touch file.txt
    nano Dockerfile
        FROM debian:jessie
        RUN apt-get update 
        RUN apt-get install -y htop
        COPY file.txt /src/file.txt
    docker build -t afonsobarrenha/debian:1.2.0 . 

    docker exec -it container_id comando

### Running Containers with Docker-Compose
    docker-compose up
    docker-compose up -d
    docker-compose ps
    docker-compose logs container_id
    docker-compose stop container_id
    docker-compose rm container_id
    docker-compose build container_id
    docker-compose run container_id comando