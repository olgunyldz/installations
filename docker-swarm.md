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
