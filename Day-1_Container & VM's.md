## 1. Docker

## 🧠 Definition:
Docker is an open-source platform used to automate the deployment, scaling, and management of applications using containers.

## 🛠 Key Features:
Lightweight

Portable

Uses a layered file system (UnionFS)

Uses Docker Engine to build and run containers

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

## 2. Container

## 🧠 Definition:

A container is a lightweight, standalone, executable package that includes everything needed to run a piece of software: code, runtime, system tools, libraries, and settings.

## 📦 Containers vs VMs:

| Feature      | Containers            | Virtual Machines            |
| ------------ | --------------------- | --------------------------- |
| Isolation    | Process-level         | Hardware-level              |
| Startup Time | Seconds               | Minutes                     |
| Size         | MBs                   | GBs                         |
| Performance  | Near-native           | Slightly lower (hypervisor) |
| OS           | Shares host OS kernel | Each has its own OS         |

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

## 3. Virtual Machine (VM)

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

Resource intensive


