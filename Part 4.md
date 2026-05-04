# DOCKER NETWORKING

## SCENARIO
A. You have Container 1 and Container 2 inside a Host Machine and they need to interact with each other.  
- Example: Container 1 is your frontend while Container 2 is your backend.  

B. You also want good separation or isolation between containers.  
- Example: Container 1 is for login, while Container 2 is for payment purposes.  

# TYPES OF DOCKER NETWORKING

### 1. Bridge Networking (Default)  
- Default network in Docker  
- Containers can communicate with each other within the same bridge network  

### 2. Host Networking  
- The container uses the host’s network directly  
- No network isolation between host and container  

#### Note:
- The container does not get its own IP (shares host network)  
- Disadvantage: Not secure (no isolation)  

### 3. Overlay Networking  
- Used for multi-host communication  
- Common in container orchestration like Docker Swarm or Kubernetes  
- Useful when you have multiple hosts  

# HOW CONTAINERS INTERACT WITH HOST MACHINE

By default, Docker uses bridge networking  

### SCENARIO 1:
- Docker creates a virtual network called "docker0" (bridge)  
- Containers connected to this bridge can communicate with each other and the host  

#### Note:
- Containers in the same default bridge network can communicate  
- But it is less isolated if everything is in one network  

### SCENARIO 2:
Using custom bridge networking  

- You can create your own bridge network  
- Containers in this network are isolated from others unless explicitly connected  

Example:
- Container 1 uses default bridge (docker0)  
- Container 2 uses custom bridge network  

→ This provides better isolation and security  

#### Note:
- Containers in the same custom bridge network can communicate using container names (built-in DNS), not just IP addresses
- Containers in the same custom bridge network can communicate using container names (DNS-based)


# COMMANDS: CREATE CONTAINER AND TEST BRIDGE NETWORKING

docker run -d --name <name of the container> nginx:latest  
→ run the container  

docker exec -it <container name> /bin/bash  
→ login to the container  

apt-get update && apt-get install iputils-ping -y  
→ install ping command  

ping <IP address of the container>  
→ test connectivity  

docker inspect <name of the container>  
→ shows container details like IP address (run this outside the container)  

docker network ls  
→ list all networks  

docker network rm <name of the network>  
→ delete specific network  


# COMMANDS: CREATE ISOLATION BETWEEN CONTAINERS

docker network create <name of the custom network>  
→ create a custom bridge network (separate subnet)  

### Attach this network to a container:

docker run -d --name <name of the container> --network=<name of the custom network> nginx:latest  
→ create container and attach to custom network  

### USING HOST NETWORK

docker run -d --name <name of the container> --network=host nginx:latest  

→ container will use host network directly  
→ Docker will not assign a separate IP (it shares the host network)  
