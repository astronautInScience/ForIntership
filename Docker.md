# Docker
# 🐳 Docker --- Complete Guide for Software Development

## 🧩 1. What Is Docker?

**Docker** is a platform that allows developers to **package
applications and their dependencies** into **containers**.\
These containers run identically on any system --- making deployment
consistent, portable, and efficient.

### 🔹 Key Concepts

  -----------------------------------------------------------------------
  Concept                       Description
  ----------------------------- -----------------------------------------
  **Container**                 A lightweight, isolated environment for
                                running an application.

  **Image**                     A read-only template that defines what's
                                inside the container.

  **Dockerfile**                A script containing instructions to build
                                an image.

  **Docker Engine**             The runtime that runs and manages
                                containers.

  **Docker Hub**                A registry for sharing and downloading
                                Docker images.
  -----------------------------------------------------------------------

### 🎯 Benefits

-   Portability (runs anywhere)
-   Isolation (independent environments)
-   Fast deployment
-   Easy scaling and automation

------------------------------------------------------------------------

## ⚙️ 2. Docker Workflow

### 🔹 The Docker Workflow

    Source Code → Dockerfile → Image → Container → Service

### Steps:

1.  **Build** -- Create an image using a `Dockerfile`
2.  **Ship** -- Push the image to a registry (like Docker Hub)
3.  **Run** -- Deploy containers on any system
4.  **Scale** -- Manage multiple containers with Compose, Swarm, or
    Kubernetes

------------------------------------------------------------------------

## 🧱 3. Building and Running Containers

### 🔹 Common Commands

``` bash
docker ps -a               # View all containers
docker run hello-world     # Run a test container
docker build -t myapp .    # Build an image from Dockerfile
docker run -p 5000:5000 myapp  # Run container
docker stop <id>           # Stop a container
docker rm <id>             # Remove container
docker rmi <id>            # Remove image
```

### 🔹 Example: Dockerizing a Flask App

**`app.py`**

``` python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from Docker!"

if __name__ == '__main__':
    app.run(host='0.0.0.0')
```

**`Dockerfile`**

``` dockerfile
FROM python:3.10
WORKDIR /app
COPY . .
RUN pip install flask
CMD ["python", "app.py"]
```

Build and run:

``` bash
docker build -t flask-app .
docker run -p 5000:5000 flask-app
```

------------------------------------------------------------------------

## 🪄 4. Docker Compose

**Docker Compose** is used to manage **multi-container** applications.

Example: Flask + MySQL

**`docker-compose.yml`**

``` yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
  db:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: appdb
```

Run:

``` bash
docker-compose up
```

------------------------------------------------------------------------

## ⚙️ 5. Key Docker Components

  Component           Description
  ------------------- -------------------------------------------------------
  **Docker Daemon**   Performs all Docker tasks, including builds.
  **Docker CLI**      Sends commands to the Docker Daemon.
  **Images**          Blueprints for containers.
  **Containers**      Running instances of images.
  **Layers**          Incremental file system changes that speed up builds.
  **Volumes**         Persist data beyond container lifecycle.
  **Networks**        Allow containers to communicate.

------------------------------------------------------------------------

## 🧩 6. Core Questions and Answers

### ❓ Q1: The main concept of Docker relies on loosely isolated environments. What are these called?

✅ **Answer:** Containers

### ❓ Q2: Which file is used as instructions on how to build a Docker image?

✅ **Answer:** Dockerfile

### ❓ Q3: Which use case for Docker is a new alternative to monolithic applications?

✅ **Answer:** Microservices

### ❓ Q4: Dockerfiles must start by defining what?

✅ **Answer:** A base layer (using `FROM` instruction)

### ❓ Q5: Which command shows all containers regardless of state?

✅ **Answer:** `docker ps -a`

### ❓ Q6: What command is used to start a new container?

✅ **Answer:** `docker run`

### ❓ Q7: Which component speeds up build time and increases reusability?

✅ **Answer:** Layers

### ❓ Q8: Which portion of Docker performs builds?

✅ **Answer:** Docker daemon

------------------------------------------------------------------------

## 🧠 7. Resource Management

Docker allows managing CPU, memory, and storage for containers.

Example:

``` bash
docker run --cpus=2 --memory="1g" myapp
docker stats             # View live usage
docker system df         # Show disk usage
docker system prune      # Clean up unused data
```

------------------------------------------------------------------------

## 🔐 8. When to Use Docker

  When to Use                        Why
  ---------------------------------- --------------------------------------
  Developing portable apps           Same environment everywhere
  Running microservices              Independent and scalable services
  Setting up dev/test environments   Fast, disposable setups
  Continuous Integration             Reproducible build/test environments
  Cloud deployment                   Works with AWS, Azure, GCP easily

------------------------------------------------------------------------

## 🧰 9. Advanced Concepts

  Feature                  Purpose
  ------------------------ ------------------------------------------
  **Docker Networking**    Connect containers with virtual networks
  **Volumes**              Persist data beyond container life
  **Multi-stage Builds**   Optimize and shrink image size
  **Swarm / Kubernetes**   Container orchestration and scaling
  **Security & Secrets**   Manage access and protect sensitive data

------------------------------------------------------------------------

## 📘 10. Learning Resources

-   [Docker Docs](https://docs.docker.com/)
-   [Docker Hub](https://hub.docker.com/)
-   [Play with Docker](https://labs.play-with-docker.com/)
-   *Book:* "Docker Deep Dive" by Nigel Poulton
-   *YouTube:* FreeCodeCamp --- *Docker Full Course*

------------------------------------------------------------------------

## 🗓️ 11. Suggested 4-Week Learning Plan

  -----------------------------------------------------------------------
  Week              Focus                   Outcome
  ----------------- ----------------------- -----------------------------
  1                 Basics, commands, and   Run and understand containers
                    Docker concepts         

  2                 Build Dockerfiles and   Containerize own projects
                    use Compose             

  3                 Networking and Volumes  Manage complex applications

  4                 CI/CD and Cloud         Apply Docker in real projects
                    Deployment              
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 🧩 12. Summary Table

  ----------------------------------------------------------------------------
  Concept              Description                   Example
  -------------------- ----------------------------- -------------------------
  **Base layer**       Starting image defined in     `FROM ubuntu:22.04`
                       Dockerfile                    

  **Container**        Running instance of an image  `docker run nginx`

  **Image**            Blueprint for containers      `docker build -t app .`

  **Layer**            Cached changes for faster     `RUN pip install flask`
                       builds                        

  **Daemon**           Background service performing `dockerd`
                       Docker operations             

  **Compose**          Tool for managing             `docker-compose up`
                       multi-container apps          
  ----------------------------------------------------------------------------

------------------------------------------------------------------------

## 🚀 Conclusion

Docker revolutionizes software development by providing a **consistent,
efficient, and portable** environment for building, testing, and
deploying applications.\
Its **container-based architecture**, **layer caching**, and **ease of
integration** make it one of the most important tools for modern
developers.
