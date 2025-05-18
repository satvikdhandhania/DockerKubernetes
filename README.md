# Docker 

## Run image 
$ docker run hello-world

$ docker run busybox echo "hello from busybox"
hello from busybox

We can use *--rm* to clean up containers automatically once they have exited

## Download image from registry 
docker pull busybox
## Show all images
$ docker images
REPOSITORY              TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
busybox                 latest              c51f86c28340        4 weeks ago         1.109 MB

## Clean up all containers
docker rm $(docker ps -a -q -f status=exited)