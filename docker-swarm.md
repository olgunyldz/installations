# An enterprise grade secure cluster:

* Manage one or more Docker nodes as a cluster
* Encrypted distributed cluster store
* Encrypted networks
* Secure join tokens


# An orchestration engine for creating mircoservices:

* API for deploying and managing microservices
* Declarative manifest files for defining apps
* Provides availability to scale apps, and perform rolling updates and rollbacks


# Install Docker CE

### Add the Docker repository:

```
sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
```

### Set up the stable repository:

```
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

### Install Docker CE:

```
sudo yum -y install docker-ce
```

### Enable and Start Docker:

```
sudo systemctl start docker && sudo systemctl enable docker
```

### Add cloud_user to the docker group:

```
sudo usermod -aG docker cloud_user
```


### Initialize the manager:

```
docker swarm init \
--advertise-addr [PRIVATE_IP]
```

### Add the worker to the cluster:

```
docker swarm join --token [TOKEN] \
[PRIVATE_IP]:2377
```

### List the nodes in the swarm:
```
docker node ls
```

### Listing nodes:

```
docker node ls
```

### Inspecting a node:
```
docker node inspect [NODE_NAME]
```

### Promoting a worker to a manager:
```
docker node promote [NODE_NAME]
```


### Demoting a manager to a worker:
```
docker node demote [NODE_NAME]
```


### Removing a node form the swarm (node must be demoted first):
```
docker node rm -f [NODE_NAME]
```

### Make a node leave the swarm:
```
docker swarm leave
```

### Getting the join-token:

```
docker swarm join-token [worker|manager]
```

### Make the node rejoin the swarm:

```
docker swarm join --token [TOKEN] \
<PRIVATE_IP>:2377
```

## Working with Services

### Creating a service:

```
docker service create -d --name [NAME] \
-p [HOST_PORT]:[CONTAINER_PORT] \
--replicas [REPLICAS] \
[IMAGE] [CMD]
```

### List services:

```
docker service ls
```

### Inspecting a service:

```
docker service inspect [NAME]
```

### Get logs for a service:

```
docker service logs [NAME]
```

### List all tasks of a service:

```
docker service ps [NAME]
```

### Scale a service up or down:

```
docker service scale [NAME]=[REPLICAS]
```

### Update a service:

```
docker service update [OPTIONS] [NAME]
```

### Create nginx_service:

```
docker service create -d --name nginx_service -p 8080:80 --replicas 2 nginx:latest
```

### List the swarm services:

```
docker service ls
```

### Inspect nginx_service:

```
docker service inspect nginx_service
```

### Find the network:

```
docker network ls --no-trunc | grep [NETOWRK_ID]
```

### View the running tasks for nginx_service:

```
docker service ps nginx_service
```

### Scale nginx_service to 3 replicas:

```
docker service scale nginx_service=3
```
