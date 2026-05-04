# DOCKER CONTAINERIZATION


### Basic Requirements

1. Know basic Python application workflow  
2. Know basic Node.js application workflow  

### Step-by-step on how to containerize an application

A. Build a Dockerfile (Example: Python app)

- Choose a base image  
  (Ex. FROM ubuntu — if you use a Python base image, you don’t need to install Python manually)

- Choose a working directory  
  (where your source code is going to be saved)

- COPY the requirements.txt to the directory  
  (this file contains the Python dependencies required to run your application)

- COPY the source code itself  

- RUN  
  (this is for configuration; since we used Ubuntu, we need to install Python first, then install dependencies)  
  Example: pip install -r requirements.txt  


### EntryPoint and CMD (Very Important)
- ENTRYPOINT and CMD are used to execute your start command  

- Difference:
  ENTRYPOINT  
  - cannot be easily changed/overwritten when running the container  
  - used for fixed executable (main command)

  CMD  
  - can be overridden when running the container  
  - used for default arguments or commands  

- You can also ignore ENTRYPOINT and just use CMD  

## Example scenario:  
- If your application runs on port 8000 by default, but port 8000 is already used in your EC2 instance,  
  CMD can be overridden to change behavior during runtime  

