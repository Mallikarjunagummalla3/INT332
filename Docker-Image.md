# Docker Image Commands
1. List Docker Images

To view all images available locally.

docker images

Example output:

REPOSITORY          TAG       IMAGE ID       CREATED         SIZE
nginx               latest    3b3a1e2e7a5b   2 days ago      133MB
my-app              v1        dcb9457e4211   1 week ago      150MB
2. Pull an Image from Docker Hub

To download a Docker image from Docker Hub (or any registry).

docker pull nginx

To pull a specific tag (version):

docker pull nginx:1.21
3. Build an Image from a Dockerfile

To build a Docker image from a Dockerfile in your current directory.

docker build -t my-image .

Explanation:

-t my-image: Specifies the name of the image (tag).

.: Refers to the current directory where the Dockerfile is located.

4. Tag an Image

To create a tag for an image. Tags are often used for versioning.

docker tag my-image myrepo/my-image:v1

This tags the my-image as myrepo/my-image:v1.

5. Push an Image to a Docker Registry

To push an image to a Docker registry (e.g., Docker Hub, private registry).

docker push myrepo/my-image:v1

Make sure you’re logged in to Docker Hub or the private registry first:

docker login
6. Remove an Image

To delete a specific image from your local machine.

docker rmi my-image

If the image is being used by a container, Docker will not let you remove it until the container is removed or stopped.

To forcefully remove an image:

docker rmi -f my-image
7. Inspect an Image

To see detailed information about an image.

docker inspect my-image

This shows metadata like layers, environment variables, build arguments, etc.

8. Build an Image from a Dockerfile (with Context)

You can specify a directory as the build context instead of using ..

docker build -t my-image /path/to/context
9. Check the History of an Image

To view the history of an image, including its layers.

docker history my-image
10. Save an Image as a Tarball

To save a Docker image into a .tar file for transferring or archiving.

docker save -o my-image.tar my-image
11. Load an Image from a Tarball

To load a Docker image from a .tar file.

docker load -i my-image.tar
12. Run a Container from an Image

To create and start a container from an image.

docker run -d --name my-container my-image

Explanation:

-d: Detached mode (runs in the background).

--name my-container: Assigns a custom name to the container.

13. Check the Size of an Image

To view the size of a specific image.

docker image ls --format "{{.Repository}}:{{.Tag}} - {{.Size}}"
14. Remove Unused Images

To remove unused Docker images (dangling images).

docker image prune

To remove all unused images, not just dangling ones:

docker image prune -a
15. View Image Layers

To see the layers of a Docker image. This is useful to understand how an image is built.

docker history --no-trunc my-image
16. Build an Image with a Specific Dockerfile

To specify a different Dockerfile for building an image.

docker build -f /path/to/Dockerfile -t my-image .
17. List All Images (with Specific Columns)

To list all images with custom columns for better readability.

docker images --format "table {{.Repository}}\t{{.Tag}}\t{{.ID}}\t{{.Size}}"
18. Remove Multiple Images

To remove multiple images in one command.

docker rmi image1 image2 image3
19. View Docker Image Digests

To view the digest (hash) of a Docker image.

docker inspect --format '{{.RepoDigests}}' my-image
20. Copy an Image from One Host to Another (via Save/Load)

To move images between different Docker hosts, you can use the docker save and docker load commands.

Save the image to a tarball:

docker save -o my-image.tar my-image

Copy the tarball to the new host using scp, FTP, or any other file transfer method.

Load the image on the new host:

docker load -i my-image.tar
