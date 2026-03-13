# Docker Volumes Commands
1. List Docker Volumes

To view all Docker volumes on your system.

docker volume ls

Example output:

DRIVER    VOLUME NAME
local     my_volume
local     another_volume
2. Create a Docker Volume

To create a new named volume.

docker volume create my_volume
3. Inspect a Docker Volume

To see detailed information about a volume, including its mount point and driver.

docker volume inspect my_volume

Example output:

[
  {
    "CreatedAt": "2021-10-01T18:53:06Z",
    "Driver": "local",
    "Labels": {},
    "Mountpoint": "/var/lib/docker/volumes/my_volume/_data",
    "Name": "my_volume",
    "Scope": "local"
  }
]
4. Remove a Docker Volume

To delete a specific volume. Note: Make sure the volume is not in use by any containers.

docker volume rm my_volume
5. Run a Container with a Volume

To create a container and mount a volume to a specific path inside the container.

docker run -d --name my_container -v my_volume:/app/data nginx

Explanation:

my_volume: The name of the volume.

/app/data: The directory in the container where the volume will be mounted.

6. Run a Container with Anonymous Volume

Docker can automatically create an anonymous volume when you don’t specify a volume name.

docker run -d --name my_container -v /app/data nginx

In this case, Docker creates an anonymous volume and mounts it to /app/data inside the container.

7. List Volumes Used by a Container

To list the volumes used by a running container.

docker inspect --format '{{ .Mounts }}' my_container
8. Copy Data from a Volume to the Host

To copy files from a volume to your host machine.

docker run --rm -v my_volume:/volume -v /path/on/host:/host busybox cp -r /volume /host

Explanation:

This uses a temporary busybox container to copy data from the my_volume volume to the host path.

9. Mount a Host Directory as a Volume

Instead of using Docker-managed volumes, you can mount a host directory as a volume.

docker run -d --name my_container -v /host/path:/container/path nginx

Example:

/host/path: Path on your host machine

/container/path: Path inside the container where the host directory will be mounted

10. Backup a Volume

You can back up a volume by copying its contents to a tar file.

docker run --rm -v my_volume:/volume -v /host/backup:/backup busybox tar czf /backup/volume_backup.tar.gz -C /volume .

Explanation:
