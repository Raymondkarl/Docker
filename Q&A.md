# DOCKER INTERVIEW QUESTIONS WITH ANSWERS


## What is Docker?

Docker is an open-source containerization platform used to build, run, and manage containers.  

In my experience, I have used Docker to:
- build Docker images  
- write Dockerfiles  
- run containers  
- and push images to registries like Docker Hub, ECR, and ACR

## How are containers different from virtual machines?

Containers are lightweight because they do not have a complete operating system.  

They only contain:
- the application  
- application dependencies  
- required system libraries  

Unlike virtual machines, which include a full operating system, containers start faster and use fewer resources.  

Example:  
If I run a Java application:
- In a container → I only need the Java runtime and dependencies  
- In a VM → I need the full OS, kernel, and system libraries  

## What is the Docker Life Cycle?

1. Write a Dockerfile  
2. Build the Docker image  
3. Run the container  
4. Push the image to a registry
   
Dockerfile:
- A set of instructions used to build a Docker image  
- Defines base image, dependencies, and commands
  
Example:  
When asked to containerize an application:
- I first write a Dockerfile  
- Then build the image using docker build  
- Then run it using docker run  
- Finally, push it to a registry like Docker Hub  

## What are the different Docker components?

- Docker Client → CLI used to interact with Docker  
- Docker Daemon → core component responsible for building, running, and managing containers. **It is the brain of Docker.**
- Docker Registry → stores Docker images  


## What is the difference between COPY and ADD?

COPY:
- Copies files from host to container  

ADD:
- Can copy files from host  
- Can also download files from a URL  

#### Note: COPY is preferred for simplicity and predictability  

## What is the difference between CMD and ENTRYPOINT?

ENTRYPOINT:
- Defines the main executable  
- Cannot be easily overridden  

CMD:
- Provides default arguments  
- Can be overridden when running the container  


## What are the networking types in Docker and what is the default?

- Bridge (default)  
- Host  
- Overlay  

## How do you isolate networking between containers?

- Use custom bridge networks  
- Assign specific containers to specific networks  
- This ensures isolation and improves security  

## What is a multi-stage build in Docker?

Multi-stage build allows you to build your application in multiple stages and copy only the required artifacts to the final image.  

Advantage:
- smaller image size  
- better security  

## What are distroless images in Docker?

Distroless images contain only:
- application  
- runtime dependencies  

They do not include:
- shell  
- package managers  

#### Note: This reduces attack surface and improves security  

## Real time challenges with Docker?

a. Docker is a single daemon process  
- This can cause a single point of failure  
- If the Docker daemon goes down, all the applications are affected  

(Example: tools like Podman address this challenge. Podman does not use a daemon, so it does not have a single point of failure, and it can run the same Docker instructions)

b. Docker daemon runs as root user  
- This is a security threat  
- Any process running as root can have adverse effects if compromised  

(Again, Podman solves this because it does not run as root)

c. Resource constraints  
- If you run too many containers on a single host, you may experience performance issues or crashes  


## What steps would you take to secure containers?

a. Use distroless images or minimal images  
- This reduces the chances of vulnerabilities  

b. Ensure that networking is configured properly  
- Use custom bridge networks to isolate containers if needed  

c. Use tools to scan container images  
- This helps detect security vulnerabilities  
## Real-time challenges with Docker

a. Single point of failure  
- Docker daemon is a single process  
- If it goes down, containers are affected  

b. Runs as root user 
- Can be a security risk  

c. Resource constraints  
- Running too many containers can affect performance  


## What steps would you take to secure containers?

a. Use distroless or minimal images  
- Reduces vulnerabilities  

b. Configure networking properly  
- Use custom networks for isolation  

c. Scan container images  
- Use tools like Docker scan or other security tools  
