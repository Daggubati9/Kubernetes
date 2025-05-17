## 1. Virtual Machine (VM)

## 🧠 Definition:

A virtual machine is a software emulation of a physical computer. It runs an operating system and applications just like a physical machine.

## 🧱 VM Structure:

            +----------------------+
            | Guest OS             |
            +----------------------+
            | Virtual Hardware     |
            +----------------------+
            | Hypervisor           |
            +----------------------+
            | Host OS              |
            +----------------------+
            | Physical Hardware    |
            +----------------------+

## 🔄 VM Flow:

            Create VM → Install OS → Deploy App

## 👎 Drawbacks (compared to containers):

            Heavy
            
            Slower startup

## 2. Container

## 🧠 Definition:

A container is a lightweight, standalone, executable package that includes everything needed to run a piece of software: code, runtime, system tools, libraries, and settings. A container is a way to package an application with all necessary dependencies and configuration. Containers are isolated, fast, and ideal for DevOps. They differ from VMs by being more efficient and lightweight. we can easily create, build, and run containers using Docker CLI.

## 🔑 Key Points:

            Portable – Run the same container anywhere: dev, test, prod.
            
            Layered – Containers are made of image layers stacked on top of each other.
            
            Base OS image – The bottom-most layer is often a minimal OS like Alpine, Ubuntu, or Debian.

## ⚖️ Containers vs Virtual Machines:

## ❓ What are Containers:

            Lightweight environments to run applications
            
            Share the host OS kernel (no need for a full OS inside)

## 🛠 How are Containers Useful:

            Fast startup (in seconds)
            
            Low overhead (small size)
            
            Easy to scale and isolate services
            
            Great for microservices and CI/CD pipelines

## 🔄 How are Containers Different from VMs:

| Feature        | Containers            | Virtual Machines                  |
| -------------- | --------------------- | --------------------------------- |
| OS             | Share host OS kernel  | Each has its own OS               |
| Size           | MBs                   | GBs                               |
| Startup Time   | Seconds               | Minutes                           |
| Resource Usage | Low                   | High                              |
| Use Case       | Microservices, DevOps | Full OS environments, legacy apps |

## 🧰 Container Structure:

            +-----------------------------+
            | Application Code            |
            +-----------------------------+
            | Dependencies (Libs/Tools)   |
            +-----------------------------+
            | Container Runtime (Docker)  |
            +-----------------------------+
            | Host OS Kernel              |
            +-----------------------------+

## 🖼 Visual Diagram : Containers vs VMs:

              Containers                        Virtual Machines
            +--------------+               +------------------------+
            | App A        |               | Guest OS A             |
            | Libraries    |               | +--------------------+ |
            | +----------+ |               | | App A              | |
            | | Runtime  | |               | +--------------------+ |
            +--------------+               +------------------------+
            | Container Engine             | Hypervisor
            | (e.g., Docker)               |
            +--------------+               +------------------------+
            | Host OS                      | Host OS
            +--------------+               +------------------------+
            | Hardware                     | Hardware
            +--------------+               +------------------------+


## 3. Docker

## 🧠 Definition:
Docker is an open-source platform used to automate the deployment, scaling, and management of applications using containers. Docker is a set of platform as a service (PaaS) products that use OS-level virtualization to deliver software in packages called containers. Docker helps you build, ship, and run applications in a lightweight, consistent, and repeatable way. Docker uses containers to make software portable and consistent.

## 📦 Docker Architecture:

            +-------------------------+
            |     Docker CLI/API     |
            +-------------------------+
                        |
            +-------------------------+
            |     Docker Daemon       |
            +-------------------------+
                        |
            +----------------+    +----------------+
            | Docker Images  |    | Docker Containers |
            +----------------+    +----------------+

## 🔄 Docker Lifecycle Flow:

            Dockerfile → docker build → Docker Image → docker run → Docker Container

## ✅ How to Run a Docker Container:

            docker run hello-world

-> Pulls the image if not present

-> Starts the container and runs the app inside it

## ✅ How to Run a Custom Container (e.g., Flask app):

            docker run -p 5000:5000 daggubati9/myapp

## ✅ How to Create a Container

Step-by-step:

## 1. Write Dockerfile

            FROM python:3.8
            COPY . /app
            WORKDIR /app
            RUN pip install -r requirements.txt
            CMD ["python", "app.py"]

## 2. Build Image

            docker build -t my-flask-app .

## 3. Run Container

            docker run -p 5000:5000 my-flask-app

## 🛠 Docker Flowchart:

            Source Code → Dockerfile → docker build → Docker Image → docker run → Container

## 🔹 Example: Run a Docker Container using Apache web Server:
            
## 🔹 1. View Running Containers

            docker ps
            
            ✅ Use: Lists all currently running containers
            
            ✅ Demo Step:
            
            Run this after starting a container to get its Container ID
            
            Show columns like container ID, image name, port mappings, status, etc.

## 🔹 2. Run an HTTPD Container with Port Mapping

            docker run -it -P 8089:80 httpd
            ✅ Use:
            
            Runs an Apache web server (httpd image)
            
            Maps host port 8089 → container port 80
            
            ✅ Demo Step:
            
            After running, visit http://localhost:8089
            
            Say: “This shows the default Apache web page. It works!”

## Docker Image:-

## What is the Difference Between a Container and an Image:

            A Docker image is like a blueprint or a recipe. It has all the instructions and files needed to create a running system. It’s read-only and doesn't change.
            
            A container, on the other hand, is the running version of that image. When we run the image, it becomes a live, working container.
            
            Think of it like baking a cake:
            
            The image is the recipe (how to make the cake).
            
            The container is the actual cake (the result of following the recipe).
            
            We can run multiple containers from the same image, just like we can bake multiple cakes from the same recipe.”
            
            
## Class and Object Difference

            “The difference between image and container is very similar to the difference between a class and an object in programming.
            
            A class is just a definition—it tells us what an object should look like.
            
            An object is the actual instance created from that class.
            
            Similarly:
            
            A Docker image is like a class—just a definition or blueprint.
            
            A container is like an object—an actual running instance based on that image.”

## ✅ Docker Image and Container Flow:-

            [Create HTML File (mydata.html)]
                          |
                          v
            [Create Dockerfile]
               (Specify base image and COPY command)
                          |
                          v
            [Build Docker Image]
               docker build -t myhttpd:1.0 .
                          |
                          v
            [Run Docker Container]
               docker run -it -p 8089:80 myhttpd:1.0
                          |
                          v
            [Access Website]
               Open browser → http://localhost:8089
                          |
                          v
            [Exec into Container (optional)]
               docker ps
               docker exec -it <container_id> bash
                          |
                          v
            [Check Directory/Logs]
               cd /usr/local/apache2/htdocs/
               ls
               docker logs <container_id> -f
                          |
                          v
            [Stop Container (optional)]
               kill <PID>  (or) docker stop <container_id>


## Example: How to Build a Docker Image:

To build a Docker image, we follow a few simple steps. First, we create the files we want inside the container—like an HTML file for a website. Next, we write a special instruction file called a Dockerfile. This file tells Docker what base image to use and what files to copy inside.

 ## 🔹 1. Create a New HTML Page

            echo "My data" > mydata.html
            
            ✅ Use: Creates a file inside the container’s file system
            
            ✅ Demo Step:
            
            Create the file inside /usr/local/apache2/htdocs/
            
## 🔹 2. Create Dockerfile

            FROM httpd:latest
            COPY mydata.html /usr/local/apache2/htdocs/

## 🔹 3. Then, I build the image using this command:

            docker build -t myhttpd:1.0 .

## 🔹 4. Finally, I run the container from that image:

            docker run -it -p 8089:80 myhttpd:1.0
            
            This will run the Apache server and show my web page when I go to http://localhost:8089.”

## sample commands Executing Inside a Running Container

            docker exec -it <container_id> bash
            
            ✅ Use: Opens a bash shell inside the container
            
            ✅ Demo Step:
            
            Run pwd, ls, and cd htdocs/
            
            Then ls to list files like index.html


## 🔹 Update Package Lists (Debian/Ubuntu containers)

            apt update
            
            ✅ Use: Refreshes package list in Debian-based containers

            apt install -y procps
            
            ✅ Use: Installs ps command (used for process listing)

## 🔹 List Running Processes Inside Container

            ps -aef
            
            ✅ Use: Shows detailed process list

## 🔹 Kill a Running Container

            kill 1
            ✅ Use:
            
            PID 1 is usually the main process in the container
            
            Killing it stops the container
            ✅ Demo Step:
            
            After kill 1, refresh the browser → it should give a server error

## 🔹 View Logs of a Container

            docker logs <container_id>
            
            Extra Options:
            
            docker logs -f <container_id>     # Follow logs in real-time
            
            docker logs -c <container_id>     # (typo in note) -c is not valid for logs
            
            ✅ Demo Step:
            
            Show how logs appear
            
            Use -f to simulate real-time monitoring


