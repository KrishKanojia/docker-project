# docker-project
This project shows how docker actually works.


**Docker**

1. **Why Containers?**
   - Different computers have different environment setups.
   - Therefore, the same application may not run in every environment.

2. **What are Containers?**
   - Containers are a way to package applications with all necessary dependencies and configurations.
   - They are portable artifacts, easily shared and moved to any environment.
   - Containers make development and deployment easier, more efficient, and synchronized.
   - They eliminate issues with packages and configurations.

3. **Docker Image and Containers**
   - We "dockerize" our application.
   - A container is a combination of layers of images.
   - The base image may be, for example, MySQL or MongoDB.
   - Taking all layers of an image together is called a Docker image.
   - Running a Docker image internally creates a container, setting up the environment, installing dependencies, and running the application.

4. **Docker Image vs Container**
   - Docker Image: A packaged artifact.
   - Docker Container: A running instance of a Docker Image, creating an environment.

5. **Docker and Virtual Machine**
   - Docker virtualizes only the application layer.
   - Docker images can communicate with the OS kernel.
   - In contrast:
     - Virtual Machines (VMs) virtualize both the application and OS kernel layers.
     - VMs have their own application and OS kernel layers.
   - Docker images are smaller in size than VMs.
   - Docker runs faster than VMs because it only virtualizes the application layer.
   - VMs can be installed on any OS, while Docker images may have compatibility issues.

**Steps to Dockerize an Application:**

1. Provide host and port in the Flask application.
2. Use `Host='0.0.0.0'` to access both local IP and localhost.
3. Create a Dockerfile:
   - `FROM [baseimage]`
   - `COPY [current directory] [docker image directory]`
   - `WORKDIR [working directory, same as docker image directory]`
   - `RUN [dependencies]`
   - `CMD [executable command] [entry-level file to run]`
4. Build the Docker Image using the command: `docker build -t welcome-app .`
5. View Docker Images: `docker images`
6. Run the Docker Image:
   - Provide host port and Docker image name.
   - Command: `docker run -p 5000:5000 welcome-app`
7. Stop a Docker Container: `docker stop [container id]`

**Push Docker Image to Docker Hub:**

8. Command to log in: `docker login`
9. Remove a Docker Image: `docker image rm -f [image name]`
10. Duplicate a Docker Image: `docker tag [current image name] [new image name]`
11. Push the Image to a Hub Repository: `docker push [image name]:[tag]`
12. Pull a Docker Image: `docker pull [image name]:[tag]`
13. Docker Run in Detach Mode: `docker run -d -p [host port no.]:[container port no.] [image name]:[tag]`

**Docker Compose**

1. Docker Compose is a tool for running multi-container Docker applications.
2. Use a `docker-compose.yaml` file to define the application configuration.
3. Commands:
   - To run the `docker-compose.yaml` file: `docker-compose up`
   - To stop a Docker Compose application: `docker-compose stop`
