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

## 🔹 Run a Docker Container using Apache web Server:
            
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

## 🔹 3. Executing Inside a Running Container

            docker exec -it <container_id> bash
            
            ✅ Use: Opens a bash shell inside the container
            
            ✅ Demo Step:
            
            Run pwd, ls, and cd htdocs/
            
            Then ls to list files like index.html

## 🔹 4. Create a New HTML Page

            echo "My data" > mydata.html
            
            ✅ Use: Creates a file inside the container’s file system
            
            ✅ Demo Step:
            
            Create the file inside /usr/local/apache2/htdocs/
            
            Access via: http://localhost:8089/mydata.html

## 🔹 5. Update Package Lists (Debian/Ubuntu containers)

            apt update
            
            ✅ Use: Refreshes package list in Debian-based containers

            apt install -y procps
            
            ✅ Use: Installs ps command (used for process listing)

## 🔹 6. List Running Processes Inside Container

            ps -aef
            
            ✅ Use: Shows detailed process list

## 🔹 7. Kill a Running Container

            kill 1
            ✅ Use:
            
            PID 1 is usually the main process in the container
            
            Killing it stops the container
            ✅ Demo Step:
            
            After kill 1, refresh the browser → it should give a server error

## 🔹 8. View Logs of a Container

            docker logs <container_id>
            
            Extra Options:
            
            docker logs -f <container_id>     # Follow logs in real-time
            
            docker logs -c <container_id>     # (typo in note) -c is not valid for logs
            
            ✅ Demo Step:
            
            Show how logs appear
            
            Use -f to simulate real-time monitoring

