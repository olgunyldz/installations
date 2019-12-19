
# Docker Install: Ubuntu

This demo was created using an Ubuntu VM. 

```
[user@ellmarquez1 ~]$ uname -r
5.0.0-37-generic
```
## Setting up the Repository

1. Ensure your *apt package index* is up to date.

   ```osboxes@osboxes:~$ sudo apt-get update```

1. Install the following apt packages to allow apt to use a repository over HTTPS:

    ```osboxes@osboxes:~$ sudo apt-get install apt-transport-https  ca-certificates  curl  software-properties-common```

3. Add Docker’s official GPG key:

   ```osboxes@osboxes:~$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -```

4. Verify that the GPG key fingerprint matches. As of publishing this guide, the fingerprint is *9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88*:
``` 
osboxes@osboxes:~$ sudo apt-key fingerprint 0EBFCD88
pub   4096R/0EBFCD88 2017-02-22
      Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid   Docker Release (CE deb) <docker@docker.com>
sub   4096R/F273FCD8 2017-02-22 
```
5. Add the repository using the `add-apt-repository` command:

    ```osboxes@osboxes:~$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" ```

## Install Docker Community Edition

1. Update the *apt package index* using the `apt-get update` command:

   ```osboxes@osboxes:~$ sudo apt-get update```

2. Install Docker Community Edition using the `apt-get install docker-ce` command:

   ```osboxes@osboxes:~$ sudo apt-get install docker-ce```
 

3. Confirm Docker installed correctly using the `docker run` command:

   ```osboxes@osboxes:~$ sudo docker run hello-world``` 

### Optional

For best practices, do not use *root*. Instead, add your user to the Docker group. For this example, our user's is named *osboxes*: 
```
osboxes@osboxes:~$ sudo usermod -a -G docker osboxes
[sudo] password for osboxes:
osboxes@osboxes:~$ 
```

Confirm the change using the `grep` command:
```
osboxes@osboxes:~$  grep docker /etc/group 
docker:x:999:osboxes
```

Once finished, log out and then log back in for changes to take effect.
