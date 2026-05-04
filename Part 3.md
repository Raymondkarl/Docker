# DOCKER - BIND MOUNTS & VOLUMES
## Key Concept

Docker is ephemeral in nature - short lived  

Persistent file storage - data does not get erased even when the system or container goes down (if using volumes)  

### Problems

No.1  
- If the host operating system goes down, the container will also go down  
- Meaning the logfile or data inside the container can be lost
  
No.2
- Classic frontend & backend system  
- They share data with each other, but if the backend goes down, the same problem exists

No.3  
- Your app (container) reads some files from the host OS  
- If the host goes down, the app will not function properly  

### Solution (Docker Storage Options)
- Docker solves this problem by providing persistent storage options:

1. Bind Mounts  
- Allows you to bind a directory from the host into the container  

Example:  
- There is a "Raymond" folder in the host machine  
- There is also a "Raymond" folder inside the container  
- They are bind together  
- If you change something in the host folder, it will reflect inside the container  
- Usually used for development (since it depends on host path)
- 
2. Volumes (Recommended)  

- Same concept as bind mounts but better lifecycle management  
- Managed using Docker CLI
- A volume is a storage managed by Docker, stored in the host machine  
- No need to provide full directory path like /Raymond/etc  

Advantages:
- Can be created, managed, and deleted using Docker CLI  
- Can use external storage (not limited to host machine)  
- Can be used as backup  
- Can be easily shared across multiple containers  
👉 With volumes, even if the container goes down, important files will not be erased  

## Commands: Docker Volume
docker volume ls  
→ shows list of volumes  

docker volume create <name of the volume>  
→ create a specific volume  

docker volume inspect <name of the volume>  
→ check details of the volume  

docker volume rm <name of the volume>  
→ delete a specific volume  

## Other Useful Commands
docker images | head -5  
→ show latest 5 images  

docker ps  
→ list running containers  

docker ps -a  
→ list all containers  

docker inspect <name of the container>  
→ show container details (mounts, IP address, etc.)  


## Commands: Build, Run, and Mount
docker build -t <name of the image> .  
→ build a docker image (must be inside directory with Dockerfile)  

docker build -t <name of the image> -f <Dockerfile_name> .  
→ build using a specific Dockerfile  

docker run -d <image_name>  
→ run container in detached mode  

docker run -d --mount source=<volume_name>,target=<path_in_container> <image_name>  
→ run container with volume mount  
- You can also add options like read-only by adding parameters  


## Important Note

To delete a volume, you need to stop the container first  
