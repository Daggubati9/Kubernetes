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
🔄 Docker Lifecycle Flow:
plaintext
Copy
Edit
Dockerfile → docker build → Docker Image → docker run → Docker Container
