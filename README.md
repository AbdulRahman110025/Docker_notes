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
                      "sudo chown username location"
above command is used when there is an error running docker "ps command" and there is an permision denied in an given location.


#Image_Commands:
The Dockerfile you provided is used to create a Docker image for a Node.js application. Each command in this Dockerfile plays a specific role in setting up the environment, copying the necessary files, installing dependencies, and defining how the application should run. Let's break down each command in detail:

### 1. `FROM node:14`

**Purpose:**  
This command sets the base image for your Docker container. Docker images are built in layers, and the base image is the first layer upon which all subsequent layers are built.

**Details:**  
- **`node:14`** refers to a pre-built Docker image that contains Node.js version 14 and its runtime environment. This image is available from Docker Hub, a public repository for Docker images.
- By specifying `node:14`, you're telling Docker to use the Node.js environment, which includes Node.js and npm (Node Package Manager). This ensures that your application has the necessary tools to run a Node.js application.

**Real-life Example:**  
Think of this like choosing a pre-configured development environment where Node.js 14 is already installed, so you don’t have to install it manually.

### 2. `WORKDIR /usr/src/app`

**Purpose:**  
This command sets the working directory inside the Docker container where your application's code will reside.

**Details:**  
- **`/usr/src/app`** is a directory path inside the container where all subsequent commands will be executed by default.
- By setting the `WORKDIR`, you don't have to specify the full path for each file operation (like copying files or running commands). Everything will happen relative to this directory.

**Real-life Example:**  
Imagine walking into a specific room in your house to work on a project. Everything you need is in that room, so you don’t have to leave to get your tools or materials.

### 3. `COPY package*.json ./`

**Purpose:**  
This command copies your `package.json` and `package-lock.json` files from your local machine into the Docker container.

**Details:**  
- The `COPY` command takes files from your local filesystem and places them in the specified location inside the Docker container.
- `package*.json` is a wildcard pattern that matches both `package.json` and `package-lock.json`. These files are crucial because they contain information about your Node.js project's dependencies and specific versions.

**Real-life Example:**  
It’s like copying a list of ingredients and their specific quantities (from a recipe) into your kitchen before you start cooking, ensuring you have everything you need.

### 4. `RUN npm install`

**Purpose:**  
This command installs the Node.js dependencies specified in the `package.json` file.

**Details:**  
- `npm install` reads the `package.json` and `package-lock.json` files and installs all the dependencies listed in them.
- This command is run inside the Docker container, ensuring that all dependencies are installed within the container’s environment.

**Real-life Example:**  
Think of this as going shopping for the ingredients listed in your recipe and stocking them in your kitchen, making sure you have everything you need to start cooking.

### 5. `COPY . .`

**Purpose:**  
This command copies all the files and directories from your local project directory into the Docker container.

**Details:**  
- The first `.` refers to the current directory on your local machine.
- The second `.` refers to the current working directory inside the Docker container (which was set earlier to `/usr/src/app` with the `WORKDIR` command).
- This command ensures that all your application files, including source code, configuration files, and other assets, are available inside the container.

**Real-life Example:**  
This is like moving all the tools, utensils, and other materials from your house into your kitchen, so everything you need to prepare your dish is within reach.

### 6. `CMD [ "npm", "start" ]`

**Purpose:**  
This command specifies the default command to run when the Docker container starts.

**Details:**  
- The `CMD` instruction defines the command that will be executed when a container is started from your image.
- In this case, `["npm", "start"]` runs `npm start`, which typically starts your Node.js application. The `start` script should be defined in your `package.json` file.

**Real-life Example:**  
This is like lighting the stove and starting to cook the dish using the recipe instructions. The ingredients and tools are all set up, and now the actual cooking process begins.

### **Summary:**
- **`FROM node:14`** sets up the Node.js environment.
- **`WORKDIR /usr/src/app`** establishes a working directory.
- **`COPY package*.json ./`** copies dependency files.
- **`RUN npm install`** installs dependencies.
- **`COPY . .`** copies all application files.
- **`CMD [ "npm", "start" ]`** starts the application.

This Dockerfile creates an environment where your Node.js application can run consistently across different systems, regardless of the underlying infrastructure.
