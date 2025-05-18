# Docker 

## Run image 
> $ docker run hello-world

> $ docker run busybox echo "hello from busybox"
hello from busybox

We can use *--rm* to clean up containers automatically once they have exited

## Download image from registry 
> docker pull busybox
## Show all images
> $ docker images
REPOSITORY              TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
busybox                 latest              c51f86c28340        4 weeks ago         1.109 MB

## Clean up all containers
```
$ docker rm $(docker ps -a -q -f status=exited)
```
In later versions of Docker, the docker container prune command can be used to achieve the same effect.
```
$ docker container prune
```
WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N] y
Deleted Containers:
4a7f7eebae0f63178aff7eb0aa39f0627a203ab2df258c1a00b456cf20063
f98f9c2aa1eaf727e4ec9c0283bcaa4762fbdba7f26191f26c97f64090360

Total reclaimed space: 212 B

## Running in detatched state and ports published
```
$ docker run -d -P --name static-site prakhar1989/static-site
e61d12292d69556eabe2a44c16cbd54486b2527e2ce4f95438e504afb7b02810
```
In the above command, -d will detach our terminal, -P will publish all exposed ports to random ports and finally --name corresponds to a name we want to give. Now we can see the ports by running the docker port [CONTAINER] command

$ docker port static-site
80/tcp -> 0.0.0.0:32769
443/tcp -> 0.0.0.0:32768

You can open http://localhost:32769 in your browser.

To stop a detached container, run docker stop by giving the container ID. In this case, we can use the name static-site we used to start the container.

$ docker stop static-site
static-site

## Reference
https://docker-curriculum.com/