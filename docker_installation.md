# installation to all environment
wget -qO- https://get.docker.com | sh

# ubuntu docker behind proxy

First create a systemd drop-in directory for the docker service
``` mkdir /etc/systemd/system/docker.service.d ```

create conf file that adds the proxy settings 
``` [Service]
Environment="HTTP_PROXY=http://proxy.example.com:80/" 
Environment="HTTP_PROXYS=http://proxy.example.com:80/" 
Environment="NO_PROXY=localhost,127.0.0.0/8,docker-registry.somecorporation.com"
```
Flush changes
``` sudo systemctl daemon-reload ```
``` sudo systemctl restart docker ```
