# DOCKER – PART 1 (MULTI-STAGE BUILD & BASICS)
## 1. Version Control Platforms
GitHub
- Used to store and manage source code
- Supports version control using Git
Docker Hub
- Used to store and distribute Docker images
- Acts as a container registry

## 2. Common Drawbacks of Docker
A. Runs with root privileges
- Docker daemon runs as root
- Potential security risk if not properly configured

B. Single point of failure (if not properly designed)
- If one container or service fails, it can affect the whole application

Better approach:
- Use microservices architecture
- Use orchestration tools like Kubernetes

## 3. Distroless Images (Security Best Practice)
- Minimal Docker image that contains only:
  • Application
  • Runtime
  • Required dependencies
- No shell
- No package manager

Example:
gcr.io/distroless/nodejs

Advantages:
- Smaller image size
- Reduced attack surface
- More secure (less OS vulnerabilities)

## 4. Multi-Stage Docker Build
- Uses multiple FROM statements in one Dockerfile
- Separates build stage and runtime stage

Example:
Build Stage
FROM node:18 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

Runtime Stage (Distroless)
FROM gcr.io/distroless/nodejs
COPY --from=builder /app /app
CMD ["app.js"]

## 5. Why Use Multi-Stage Build?
- Smaller image size
- Cleaner production image
- No unnecessary files (like source code and build tools)
- Better security

## 6. Key Concept Summary

Multi-stage build
→ separates build and runtime environments

Distroless image
→ minimal and secure runtime image

Combined benefit:
→ Smaller, faster, and more secure Docker images


## Interview-Ready Answer

Multi-stage Docker builds allow us to separate the build environment from the runtime environment, which reduces image size and removes unnecessary dependencies. When combined with distroless images, it improves security by minimizing the attack surface and eliminating unused OS components.
