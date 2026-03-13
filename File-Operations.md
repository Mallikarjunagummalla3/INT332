# Docker File Operations
1. Copy Files from Host to Container

To copy a file or directory from your host machine to a running container.

docker cp <host_path> <container_name_or_id>:<container_path>

Example:

docker cp /path/to/local/file.txt my-container:/path/to/container/destination

<host_path>: Path to the file or directory on your local system.

<container_name_or_id>: The container's name or ID.

<container_path>: The path inside the container where you want to copy the file or directory.

2. Copy Files from Container to Host

To copy a file or directory from a container to your host machine.

docker cp <container_name_or_id>:<container_path> <host_path>

Example:

docker cp my-container:/path/to/container/file.txt /path/to/local/destination

<container_path>: The file or directory path inside the container.

<host_path>: The destination path on your local system.

3. View Files Inside a Container

To view files inside a running container, you can open a shell inside the container using docker exec:

docker exec -it <container_name_or_id> bash

Once inside, you can navigate the container's filesystem using commands like ls, cd, cat, vi, etc.

Example:

docker exec -it my-container bash
# Now you are inside the container shell
ls /path/to/container/
4. Move Files Inside a Container

To move files within the container, you can use basic Linux commands like mv once you're inside the container.

docker exec -it <container_name_or_id> mv <source_path> <destination_path>

Example:

docker exec -it my-container mv /tmp/myfile.txt /usr/share/nginx/html/
5. Remove Files from a Container

To delete files from a container, use the rm command after accessing the container shell:

docker exec -it <container_name_or_id> rm <file_path>

Example:

docker exec -it my-container rm /tmp/myfile.txt

You can also remove entire directories using the -r flag with rm:

docker exec -it my-container rm -r /path/to/directory
6. Create a New File Inside a Container

To create a new file in a container, you can use docker exec with a text editor or the echo command:

docker exec -it <container_name_or_id> bash -c "echo 'Hello, Docker!' > /path/to/container/newfile.txt"

Example:

docker exec -it my-container bash -c "echo 'Welcome to Docker!' > /usr/share/nginx/html/index.html"

Alternatively, use a text editor inside the container, like vi or nano (if available):

docker exec -it my-container vi /path/to/container/newfile.txt
7. List Files in a Container

To list files inside a specific directory of a running container, use:

docker exec -it <container_name_or_id> ls <container_directory>

Example:

docker exec -it my-container ls /usr/share/nginx/html
8. Create a Directory Inside a Container

To create a new directory inside a running container:

docker exec -it <container_name_or_id> mkdir /path/to/container/new_directory

Example:

docker exec -it my-container mkdir /usr/share/nginx/html/images
9. Download Files Inside a Container

If you need to download files inside a container from the internet, you can use tools like curl or wget. First, access the container's shell:

docker exec -it <container_name_or_id> bash

Then, install a tool like curl or wget (if it's not already installed) and download the file:

apt-get update && apt-get install wget
wget https://example.com/file.zip
10. Create a File in the Container with Dockerfile

When building an image, you can create files directly in the Docker image by copying them from your local machine using a Dockerfile:

Example Dockerfile to copy a local file into a container:

FROM nginx
COPY ./local/file.txt /usr/share/nginx/html/

Build the image:

docker build -t my-nginx .
11. Mount Local Directory as Volume in a Container

To mount a local directory to a container so that the container can read/write to it, use the -v or --mount option when running the container:

docker run -d -v /path/on/host:/path/in/container --name my-container nginx

This will sync files between the host and container at the specified paths.

12. Sync Files Between Host and Container (Two-Way Sync)

You can create a persistent bidirectional sync between the host and the container by using Docker volumes or bind mounts. This allows files to be read/written from both the host and container.

docker run -d -v /path/on/host:/path/in/container --name my-container nginx
