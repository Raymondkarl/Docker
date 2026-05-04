# DOCKER COMMANDS 

### 1. Pull image from registry
- docker pull |image-name|
  
Example: docker pull nginx

### 2. Build Docker image (if using your own app)
- docker build -t |image-name| .

Example: docker build -t my-app .

### 3. List Docker images
- docker images

### 4. Run container
- docker run |image-name|

#### A. Run container in background
- docker run -d |image-name|

#### B. Run container with name
- docker run -d --name |container-name| |image-name|

#### C. Run container with port mapping
- docker run -d --name |container-name| -p |host-port|:|container-port| |image-name|

**Example: docker run -d --name nginx-container -p 8080:80 nginx**


### 5. List containers
- docker ps

#### A. List all containers (including stopped)
- docker ps -a

### 6. View logs 
- docker logs |container-name|

#### A. Follow logs (real-time)
- docker logs -f |container-name|

### 7. Execute command inside container
- docker exec -it |container-name| /bin/bash

### 8. Inspect container details
- docker inspect |container-name|

### 9. Stop container
- docker stop |container-name|

### 10. Start container
- docker start |container-name|

### 11. Remove container (must be stopped)
- docker rm |container-name|

### 12. Remove image
- docker rmi |image-name|

# DOCKER NETWORK COMMANDS

### 1. List networks
- docker network ls

### 2. Create network
- docker network create |network-name|

### 3. Run container with network
- docker run -d --name |container-name| --network=|network-name| |image-name|

### 4. Remove network
- docker network rm |network-name|

# DOCKER VOLUME COMMANDS

### 1. List volumes
- docker volume ls

### 2. Create volume
- docker volume create |volume-name|

### 3. Inspect volume
- docker volume inspect |volume-name|

### 4. Run container with volume
- docker run -d --mount source=|volume-name|,target=|path-in-container| |image-name|

### 5. Remove volume (must not be in use)
- docker volume rm |volume-name|
