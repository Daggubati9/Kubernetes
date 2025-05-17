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

