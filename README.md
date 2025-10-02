Docker Image Commands:

To build an image form dockerfile docker build -t <image_name>: . -t = tag . = current working dir

To get the list of docker images docker images

To pull the docker images form dockerhub automatically docker pull <image_name> By default it will download the latest.To download specific version mention version. docker pull <image_name>:

To get full information of an image docker inspect <image_name/ID>

To delete a stopped images docker rmi <Image_name/ID>

To delete all images docker rmi $(docker images) (or) docker rmi docker images

Docker container Commands:

To create a container docker create <image_name/ID>

To start a container docker start <container_name/ID>

To stop a container docker stop <image_name/ID>

To know the list of running containers docker ps

To know the list of running container IDs docker ps -q -q = IDs

To know the list of running & stopped containers docker ps -a -a = all

To know the list of running & stopped containers IDs docker ps -aq

To get list of stopped containers docker ps -a | grep -i Exited

To delete a stopped container docker rm <Container_name/ID> use -f to delete forcefully

To run a container (It will download the image and starts the container) docker run <image_name> (or) docker run -it <image_name> docker run <image_name>: (or) docker run -it <image_name>:

-it = input terminal

To send the foreground container to run background use: cntr+p+q To sptop the foreground container use: cntrl+c

To run a container at backgroud docker run -d <Image_name>: -d = detach mode

To get full information of a container docker inspect <container_ID/name>

To check the container logs docker logs <container_ID/name>

To check live logs of a container docker logs -f --tail <container_ID/name>

Assign a name to a container docker run -d (or) -it -p <host_port>:<container_port> --name <container_name> <image_name>:

To login to running container docker exec -it <container_ID/name>

Port Forwarding:

To assign a port to a container docker run -d (or) -it -p <host_port>:<container_port> <image_name>: -p = port To access the container use host_ip:host_port in browser

Docker Network Commands

To check the list of networks docker network ls

To create a network docker network create <network_name>

To run a container on a specific network docker run -d --name <container_name> --network <already_created_network_name> <Image_name>: [OR] docker run -d --name <container_name> --net <already_created_network_name> <Image_name>:

To Install docker compose:

curl -L https://github.com/docker/compose/releases/download/2.24.5/docker-compose-`uname -s-uname -m` -o /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose

docker compose

Docker Compose commands:

docker compose up -d docker compose down

Docker Volume commands:

Two types: Named volumes - Can be managed by docker commands like inpect, prune Unnamed volumes

To create a docker volume docker volume create

docker volume inspect <volume_name>

docker run -d -p<host_port>:<container_port> -v <host_volume>:<container_volume> :

docker run -d -p 80:80 -v /home/centos/nginx_folder:/usr/share/nginx/html nginx The data which is in nginx_folder will reflect in html page

we should use volumes for database applications
