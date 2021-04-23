## Installation
* 1.Open a new terminal and type in:
```shell
$ sudo apt-get install docker-compose docker-ce
```
* 2.Check the version of the installed docker. 
```shell
$ sudo docker version
```
* 3.Start the `Docker` service
```shell
$ sudo systemctl start docker
```
* 4.Set up to start automatically
```shell
$ sudo systemctl enable docker
```
* 5.Finally, test `Docker`
```shell
$ sudo docker run hello-world
```

> When you see something like this, it mean it works:
```shell
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
b8dfde127a29: Pull complete 
Digest: sha256:f2266cbfc127c960fd30e76b7c792dc23b588c0db76233517e1891a4e357d519
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```