# Docker Basic Commands
1. Docker Version

Check the version of Docker installed on your system.

docker --version
2. Docker Info

Get detailed information about your Docker setup, including the number of containers, images, and volumes.

docker info
3. List Running Containers

To list all running containers.

docker ps

Example output:

CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS     NAMES
f2a221cd06ff   nginx     "/docker-entrypoint.…"   2 minutes ago   Up 2 minutes   80/tcp    my-nginx
4. List All Containers (Including Stopped)

To list all containers (both running and stopped).

docker ps -a
5. Start a Stopped Container

To start a stopped container.

docker start <container_name_or_id>

Example:

docker start my-nginx
6. Stop a Running Container

To stop a running container.

docker stop <container_name_or_id>

Example:

docker stop my-nginx
7. Restart a Container

To restart a running or stopped container.

docker restart <container_name_or_id>

Example:

docker restart my-nginx
8. Remove a Container

To remove a stopped container.

docker rm <container_name_or_id>

Example:

docker rm my-nginx
9. Run a Container

To create and start a new container from an image.

docker run -d --name <container_name> <image_name>

Example:

docker run -d --name my-nginx-container nginx

Explanation:

-d: Detached mode (runs in the background).

--name my-nginx-container: Assigns a custom name to the container.

10. Run a Container with Port Mapping

To run a container and map container ports to host machine ports.

docker run -d -p <host_port>:<container_port> <image_name>

Example:

docker run -d -p 8080:80 nginx

Explanation:

Maps container port 80 to host port 8080.

11. View Container Logs

To view the logs of a running or stopped container.

docker logs <container_name_or_id>

Example:

docker logs my-nginx

For real-time logs:

docker logs -f my-nginx
12. Run a Command in a Running Container

To execute a command inside a running container (e.g., to open a bash shell).

docker exec -it <container_name_or_id> <command>

Example:

docker exec -it my-nginx bash

Explanation:

-it: Interactive mode (allows interaction with the container).

13. Inspect a Container

To get detailed information about a container (e.g., its networking, mounts, and environment).

docker inspect <container_name_or_id>

Example:

docker inspect my-nginx
14. List Docker Images

To list all Docker images available locally.

docker images
15. Pull an Image

To download a Docker image from Docker Hub (or any other registry).

docker pull <image_name>

Example:

docker pull nginx
16. Build an Image

To build a Docker image from a Dockerfile in your current directory.

docker build -t <image_name> .

Example:

docker build -t my-app .

Explanation:

-t my-app: Tags the image with the name my-app.

.: Refers to the current directory where the Dockerfile is located.

17. Tag an Image

To tag a Docker image (useful for versioning).

docker tag <image_id> <repository_name>:<tag>

Example:

docker tag my-app myrepo/my-app:v1
18. Remove an Image

To delete a Docker image from your local machine.

docker rmi <image_name_or_id>

Example:

docker rmi my-app
19. Remove Unused Images

To remove all unused (dangling) images.

docker image prune
20. List Docker Volumes

To list all Docker volumes on your system.

docker volume ls
21. Create a Docker Volume

To create a new volume.

docker volume create <volume_name>

Example:

docker volume create my-volume
22. Remove a Docker Volume

To remove a Docker volume.

docker volume rm <volume_name>

Example:

docker volume rm my-volume
23. List Docker Networks

To list all Docker networks.

docker network ls
24. Create a Docker Network

To create a new Docker network.

docker network create <network_name>

Example:

docker network create my-network
25. Inspect a Docker Network

To inspect a Docker network for detailed information.

docker network inspect <network_name>

Example:

docker network inspect my-network
