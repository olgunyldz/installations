# installation to all environment
wget -qO- https://get.docker.com | sh

## ubuntu docker behind proxy

First create a systemd drop-in directory for the docker service
``` mkdir /etc/systemd/system/docker.service.d ```

### create conf file that adds the proxy settings 

``` [Service]
Environment="HTTP_PROXY=http://proxy.example.com:80/" 
Environment="HTTP_PROXYS=http://proxy.example.com:80/" 
Environment="NO_PROXY=localhost,127.0.0.0/8,docker-registry.somecorporation.com"
```
### Flush changes

``` sudo systemctl daemon-reload ```

### restart docker

``` sudo systemctl restart docker ```


### add proxy to docker file

Create/edit ~/.docker/config.json

```{
 "proxies":
 {
   "default":
   {
     "httpProxy": "http://localhost:3128",
     "httpsProxy": "http://localhost:3128",
     "noProxy": "localhost"
   }
 }
}

```

### add proxy settings to docker file

```
FROM ubuntu:16.04
LABEL maintainer="olgun.yldz@gmail.com"

RUN echo http proxy: ${http_proxy} ${HTTP_PROXY}
RUN echo https proxy: ${https_proxy} ${HTTPS_PROXY}

RUN apt-get update
RUN apt-get install -y python3
```

### run command line in docker container

```
docker container run -it --name <container-name> <image-id>

```

### run docker container with predefined port expose

```
docker container run -d -p 80:80 <image-id>

```

### run docker container with random port expose

```
docker container run -d -P<image-id>

```
