## Installation

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

Apply executable permissions:

```
sudo chmod +x /usr/local/bin/docker-compose
```


build: Build or rebuild services
bundle: Generate a Docker bundle from the Compose file
config: Validate and view the Compose file
create: Create services
down: Stop and remove containers, networks, images, and volumes
events: Receive real time events from containers
exec: Execute a command in a running container
help: Get help on a command
images: List images
kill: Kill containers
logs: View output from containers
pause: Pause services
port: Print the public port for a port binding
ps: List containers
pull: Pull service images
push: Push service images
restart: Restart services
rm: Remove stopped containers
run: Run a one-off command
scale: Set number of containers for a service
start: Start services
stop: Stop services
top: Display the running processes
unpause: Unpause services
up: Create and start containers
version: Show the Docker-Compose version information



### sample docker-compose.yml

```
version: '3'
services:
  ghost:
    container_name: ghost
    image: ghost:latest
    ports:
      - "80:2368"
    environment:
      - database__client=mysql
      - database__connection__host=mysql
      - database__connection__user=root
      - database__connection__password=P4SSw0rd0!
      - database__connection__database=ghost
    volumes:
      - ghost-volume:/var/lib/ghost
    networks:
      - ghost_network
      - mysql_network
    depends_on:
      - mysql

  mysql:
    container_name: mysql
    image: mysql:5.7
    environment:
      - MYSQL_ROOT_PASSWORD=P4SSw0rd0!
    volumes:
      - mysql-volume:/var/lib/mysql
    networks:
      - mysql_network

volumes:
  ghost-volume:
  mysql-volume:

networks:
  ghost_network:
  mysql_network:

```
