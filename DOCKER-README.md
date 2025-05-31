# 🐳 Docker Quick Reference Guide

## Core Concepts

### Docker
- Platform for containerizing applications
- Package applications with all dependencies
- Run anywhere Docker is installed

### Container
- Lightweight, isolated environment
- Contains everything needed to run an app
- Portable and consistent across environments

### Image
- Read-only template for containers
- Contains app code, dependencies, and config
- Like a blueprint for containers

## Essential Commands

### Images
```bash
docker image ls          # List images
docker pull image_name   # Download image
docker rmi image_name   # Remove image
```

### Containers
```bash
docker run -it image_name    # Run container
docker container ls          # List running containers
docker exec -it container_name command  # Run command in container
docker stop container_name   # Stop container
docker rm container_name     # Remove container
```

## Port Mapping & Environment Variables
```bash
# Port mapping
docker run -p host_port:container_port image_name

# Environment variables
docker run -e KEY=value image_name
```

## Node.js Dockerfile Example
```dockerfile
FROM node:14
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

## Docker Compose
```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
```

### Compose Commands
```bash
docker compose up        # Start services
docker compose up -d    # Start in background
docker compose down     # Stop services
```

## Best Practices
1. Use specific version tags
2. Keep images small
3. Use .dockerignore
4. Run as non-root
5. Use environment variables
6. Implement health checks
7. Use Docker Compose for multi-container apps

## Quick Tips
- Use `-it` for interactive containers
- Use `-d` for detached mode
- Use `-p` for port mapping
- Use `-e` for environment variables
- Use `--name` to name containers

## Common Use Cases
1. Development environments
2. Microservices
3. CI/CD pipelines
4. Testing environments
5. Production deployments

## Resources
- [Docker Documentation](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Docker Compose Documentation](https://docs.docker.com/compose/) 