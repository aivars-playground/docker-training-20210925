Docker
=
An image is a read-only template with instructions for creating a Docker container.  
A container is a runnable instance of an image.  

Dockerfile - instruction how to build a container
Docker Compose - build/run multiple images, define a network  
Docker Swarm - define a service; swarm is a cluster of docker manager and worker nodes, can be run locally (one manager ... per server)

BASICS
=
```shell
#run shell on latest alpine linux & exit
docker container run --name test alpine sh
#or shorter
docker run --name test alpine sh

#list all (including exited) containers
docker ps -a
> CONTAINER ID   IMAGE     COMMAND   CREATED              STATUS                          PORTS     NAMES
> 85827e80da81   alpine    "sh"      About a minute ago   Exited (0) About a minute ago             test

#run exited container again
docker container start test
#or shorter
docker start test

#unless shell has been started with interactive terminal (it) ,  restarting container with i would not work
docker start -i test 

$ not sure how to use run with -t
docker container run -t --name testwithterminal alpine sh
#Ctrl +c would exit and kill the process`


# -i without -t accepts commands nd returns weird output (just out, no sell prompt: ""
docker container run -i --name testwithinteractive alpine sh
> pwd     #type in
> /       #get response
# Ctrl + D would kill process, Ctrl + C would interact within the shell, not with docker


docker container run -it --name testwithinteractiveterminal alpine sh
> / # pwd   #type in, "/ #" is sh default prompt  `<working dir> + "#"` !!!
> /         #get response
# Ctrl + D would kill process, Ctrl + C would interact within the shell, not with docker
# use Ctrl + P + Q to exit interactive mode and leave container running

#would run stopped container with correct -it, this time no need for t, it eas created earlier???
docker start -i testwithinteractiveterminal  

#attach to running container
docker attach testwithinteractiveterminal


```