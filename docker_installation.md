# Docker Install: Centos

This demo was created using an Centos. 

```
[cloud_user@olgunyildiz1c ~]$ uname -r
CentOS Linux release 7.7.1908 (Core)
```
## Setting up the Repository

1. Ensure all necassary packages has been installed.

   ```[cloud_user@olgunyildiz1c ~]$ sudo yum install -y yum-utils device-mapper-persistent-data lvm2```

2. Add repository in order to install the version of Docker

    ```[cloud_user@olgunyildiz1c ~]$ sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo```
    

## Install Docker Community Edition

1. Install Docker Community Edition using the `sudo yum install docker-ce` command:

   ```[cloud_user@olgunyildiz1c ~]$ sudo yum install docker-ce```
 
2. to enable  docker `sudo systemctl enable docker` command:

   ```[cloud_user@olgunyildiz1c ~]$ sudo systemctl enable docker```
   
3. to enable and start docker `sudo systemctl start docker` command:

   ```[cloud_user@olgunyildiz1c ~]$ sudo systemctl start docker```

4. Confirm Docker installed correctly using the `docker run` command:

   ```[cloud_user@olgunyildiz1c ~]$ sudo docker run hello-world``` 

### Optional

For best practices, do not use *root*. Instead, add your user to the Docker group. For this example, our user's is named *osboxes*: 
```
[cloud_user@olgunyildiz1c ~]$ sudo usermod -a -G docker cloud_user
[sudo] password for osboxes:
[cloud_user@olgunyildiz1c ~]$ 
```

Confirm the change using the `grep` command:
```
[cloud_user@olgunyildiz1c ~]$  grep docker /etc/group 
docker:x:999:cloud_user
```

Once finished, log out and then log back in for changes to take effect.
