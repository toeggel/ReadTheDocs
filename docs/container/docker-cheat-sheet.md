# Docker-Cheat-Sheet

Following summary was generated by ChatGPT based on a conversation I had with it.

## **1. Docker Images and Tags**
- **Default Tag (`latest`)**:
  - If no tag is specified during a build, Docker assigns the `latest` tag by default.
  - Example: `docker build -t myapp .` creates `myapp:latest`.

- **Versioned Tags**:
  - Use versioned tags (e.g., `myapp:1.0`) to track changes and ensure reproducibility.
  - Example: `docker build -t myapp:1.0 .`.

- **Best Practices**:
  - Use semantic versioning (e.g., `1.0.0`, `1.1.0`).
  - Optionally maintain a `latest` tag for the most recent version.
  - Automate tagging in CI/CD pipelines using build numbers, commit hashes, or timestamps.

- **Cleaning Up Images**:
  - Remove dangling (unused) images: `docker image prune`.
  - Remove all unused images: `docker image prune -a`.

---

## **2. Docker Containers**
- **Lifecycle**:
  - Containers are ephemeral; any data stored inside a container is lost when it is removed.
  - Use volumes or bind mounts to persist data beyond the container lifecycle.

- **Recreating Containers**:
  - Containers must be removed before being recreated.
  - Use `docker-compose down` followed by `docker-compose up` to safely recreate containers.

- **Inspecting Containers**:
  - Use `docker ps` to list running containers.
  - Use `docker inspect <container_id>` to view detailed container information.

---

## **3. Docker Volumes**
- **Purpose**:
  - Volumes persist data independently of the container lifecycle.
  - Ideal for databases, file storage, or any data that must survive container recreation.

- **Using Volumes**:
  - Define volumes in `docker-compose.yml`:
    ```yaml
    volumes:
      my-volume:
    services:
      my-service:
        volumes:
          - my-volume:/path/in/container
    ```
  - List volumes: `docker volume ls`.
  - Remove unused volumes: `docker volume prune`.

- **Bind Mounts**:
  - Use bind mounts to map a host directory to a container path:
    ```yaml
    volumes:
      - ./data:/path/in/container
    ```

---

## **4. Docker Compose**
- **Service Configuration**:
  - Define services in `docker-compose.yml` with `image`, `build`, `ports`, and `volumes`:
    ```yaml
    services:
      my-service:
        image: myapp:1.0
        build:
          context: .
          dockerfile: Dockerfile
        ports:
          - "8080:8080"
        volumes:
          - my-volume:/data
    ```

- **Ports**:
  - Use the `ports` directive to map container ports to host ports:
    ```yaml
    ports:
      - "8080:8080" # Host:Container
    ```
  - Avoid port conflicts by assigning unique host ports for each service.

- **Rebuilding Services**:
  - Force a rebuild of images: `docker-compose up --build`.
  - Pull updated images: `docker-compose pull`.

---

## **5. Dockerfile**
- **EXPOSE Directive**:
  - Documents the ports the container listens on but does not map them to the host.
  - Example:
    ```docker
    EXPOSE 8080
    ```

- **Best Practices**:
  - Use multi-stage builds to reduce image size:
    ```docker
    FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
    RUN dotnet build
    FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS runtime
    COPY --from=build /app /app
    ```
  - Keep the `Dockerfile` clean and modular.

---

## **6. Cleaning Up Docker Resources**
- **Images**:
  - Remove unused images: `docker image prune`.
  - Remove specific images: `docker rmi <image_id>`.

- **Containers**:
  - Stop and remove containers: `docker rm -f <container_id>`.

- **Volumes**:
  - Remove unused volumes: `docker volume prune`.

- **Networks**:
  - Remove unused networks: `docker network prune`.

---

## **7. Debugging and Verification**
- **Inspect Running Containers**:
  - Use `docker ps` to list running containers.
  - Use `docker logs <container_id>` to view logs.

- **Verify Ports**:
  - Check mapped ports in `docker-compose.yml` or with `docker ps`.
  - Avoid conflicts by assigning unique host ports.

- **Test Changes**:
  - Add unique log messages or version numbers to verify the latest image is running.

---

## **8. Automating with CI/CD**
- Automate builds and tagging:
  ```bash
  docker build -t myapp:$(git rev-parse --short HEAD) .
  ```
- Push images to a registry (e.g., Docker Hub, Azure Container Registry):
  ```bash
  docker push myapp:1.0
  ```

---
