# Container commands

### docker container run:

* --help Print usage
* --rm Automatically remove the container when it exits
* -d, --detach Run container in background and print container ID
* -i, --interactive Keep STDIN open even if not attached
* --name string Assign a name to the container
* -p, --publish list Publish a container's port(s) to the host
* -t, --tty Allocate a pseudo-TTY
* -v, --volume list Mount a volume (the bind type of mount)
* --mount mount Attach a filesystem mount to the container
* --network string Connect a container to a network (default "default")


###Create a container and attach to it:
```
docker container run –it busybox
```

### Create a container and run it in the background:

```
docker container run –d nginx
```

### Create a container that you name and run it in the background:

```
docker container run –d –name myContainer busybox
```

### Exposing:

* Expose a port or a range of ports
* This does not publish the port
* Use --expose [PORT]

```
docker container run --expose 1234 [IMAGE]
```

### Publishing:

* Maps a container's port to a host`s port
* -p or --publish publishes a container's port(s) to the host
* -P, or --publish-all publishes all exposed ports to random ports

```
docker container run -p [HOST_PORT]:[CONTAINER_PORT] [IMAGE]
docker container run -p [HOST_PORT]:[CONTAINER_PORT]/tcp -p [HOST_PORT]:[CONTAINER_PORT]/udp [IMAGE]
docker container run -P
```

### Lists all port mappings or a specific mapping for a container:

```
docker container port [Container_NAME]
```

### Show information logged by a running container:

```
docker container logs [NAME]
```

### Show information logged by all containers participating in a service:

```
docker service logs [SERVICE]
```

