# Docker Container Commands
1. List Running Containers

To view all currently running containers.

docker ps

Example output:

CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS     NAMES
4f7bc3c4c5f2   nginx     "/docker-entrypoint.…"   2 minutes ago   Up 2 minutes   80/tcp    my-nginx-container
2. List All Containers (Including Stopped)

To view all containers, including those that are stopped.

docker ps -a
3. Start a Stopped Container

To start a stopped container.

docker start my-container
4. Stop a Running Container

To stop a running container.

docker stop my-container
5. Restart a Container

To restart a container.

docker restart my-container
6. Remove a Container

To remove a container (stopped containers only).

docker rm my-container

You can remove multiple containers at once:

docker rm container1 container2
7. Run a New Container

To run a new container from an image.

docker run -d --name my-container nginx

Explanation:

-d: Runs the container in detached mode (in the background).

--name my-container: Assigns a name to the container.

nginx: The image to use for creating the container.

8. Attach to a Running Container

To attach to the running container’s console and interact with it.

docker attach my-container
9. Execute a Command Inside a Running Container

To run a command inside a running container.

docker exec -it my-container bash

Explanation:

-it: Combines two flags, -i (interactive) and -t (allocate a pseudo-TTY).

bash: Launches a bash shell inside the container.

10. View Container Logs

To view logs from a running or stopped container.

docker logs my-container

To view logs in real-time:

docker logs -f my-container
11. Get Container Info (Inspect Container)

To view detailed information about a container.

docker inspect my-container

This command shows information like mount points, network settings, environment variables, etc.

12. View Resource Usage of Containers

To see resource usage like CPU and memory for running containers.

docker stats
13. Pause a Running Container

To pause a running container (suspend all processes).

docker pause my-container
14. Unpause a Paused Container

To unpause a paused container.

docker unpause my-container
15. Check Container’s IP Address

To find the IP address of a running container.

docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' my-container
16. Commit Changes to a Container

To create a new image from a running container's changes.

docker commit my-container my-new-image
17. Copy Files from Container to Host

To copy files from a container to your local machine.

docker cp my-container:/path/to/file /host/path
18. Copy Files from Host to Container

To copy files from your local machine to a container.

docker cp /host/path my-container:/path/to/destination
19. List Docker Containers and Their Ports

To check the ports exposed by containers.

docker ps --format "table {{.Names}}\t{{.Ports}}"
20. Remove All Stopped Containers

To remove all stopped containers in one command.

docker container prune
21. Run a Container with Port Mapping

To run a container and map a port from the container to your host.

docker run -d -p 8080:80 nginx

Explanation:
