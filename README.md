# Docker_notes
revision for docker
## definition
It is like a box where all the requrement related for the application to run resides there . requirements like libraries, code, files etc. example would be suppose i have created note_taking application in my system . its is running locally but what if i want to run the same application to other system or my friend called me and asked for this application for him . however that application is not running to any other system. thats when containerization comes to an picture. containers allows you to run any application in any system no matter what the reqiremnent is. Docker is an containerized application ,
# terminologies : -
DockerCLI:
1) systemctl status Docker = it allows you to see if the Docker application is running or not.
2) Docker ps = docker ps provides a list of the Docker containers on your machine. You can use it to check whether a     container is running, display container sizes, and find stopped containers that you need to restart or remove.****
3)   run         Create and run a new container from an image
4)   exec        Execute a command in a running container
5)   ps          List containers
6)   build       Build an image from a Dockerfile
7)   pull        Download an image from a registry
8)   push        Upload an image to a registry
9)   images      List images
10)  login       Log in to a registry
11)  logout      Log out from a registry
12)  search      Search Docker Hub for images
13)  version     Show the Docker version information
15)  info        Display system-wide information

# Process behind making containers:
well there is a process of making containers . first there is dockerfile (2) docker Image (3) container. lets understand each one by one.
Dockerfile -> Docker Image -> Docker container
Above Formula shows the life cycle behind container..
= to build docker image from Docker file the command is (Docker build)
= to make container from image the command is (Docker run)
## Some important command
       docker run -d -p 80:80 --name nginx-box nginx:latest
-d: Runs the container in detached mode, meaning it runs in the background and does not block your terminal.
-p 80:80: Maps port 80 of the container to port 80 on the host, so you can access the Nginx server via the host's IP address.
--name nginx-box: Assigns the name nginx-box to the container, which makes it easier to manage.
nginx:latest: Specifies the image to use (nginx) and the tag (latest).
### nginx:latest 
When you use the tag nginx:latest in your Docker commands, you're specifying that you want to use the most up-to-date version of Nginx that has been published to Docker Hub
