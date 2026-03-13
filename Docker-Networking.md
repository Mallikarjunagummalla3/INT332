# Docker Networking Commands
1. List Docker Networks

Shows all available Docker networks.

docker network ls

Example output networks:

bridge

host

none

2. Inspect a Network

Shows detailed information about a specific network.

docker network inspect bridge
3. Create a Network

Creates a custom Docker network.

docker network create my-network
4. Run a Container on a Specific Network
docker run -d --name container1 --network my-network nginx
5. Connect a Running Container to a Network
docker network connect my-network container1
6. Disconnect a Container from a Network
docker network disconnect my-network container1
7. Remove a Network
docker network rm my-network
8. Run Two Containers in Same Network
docker network create app-network

docker run -d --name app1 --network app-network nginx

docker run -d --name app2 --network app-network nginx

Now containers app1 and app2 can communicate using container names.

9. Run Container with Port Mapping
docker run -d -p 8080:80 nginx

Explanation:

host_port : container_port

Example:

8080 → Host machine

80 → Inside container

Access in browser:

http://localhost:8080
10. Check Container Network
docker inspect container1

💡 Bonus command (good for your repo):

Check container IP address

docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container1
