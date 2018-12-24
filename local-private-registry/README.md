## Local private registry

```
$ docker container run -d -p 5000:5000 --name registry registry
```

```
$ docker pull hello-world
```

```
$ docker run hello-world

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

```
$ docker tag hello-world 127.0.0.1:5000/hello-world
```

```
$ docker image ls
REPOSITORY                                            TAG                 IMAGE ID            CREATED             SIZE
registry                                              latest              9c1f09fe9a86        3 days ago          33.3MB
127.0.0.1:5000/hello-world                            latest              4ab4c602aa5e        3 months ago        1.84kB
hello-world                                           latest              4ab4c602aa5e        3 months ago        1.84kB
```

```
$ docker push 127.0.0.1:5000/hello-world
The push refers to repository [127.0.0.1:5000/hello-world]
428c97da766c: Pushed
latest: digest: sha256:1a6fd470b9ce10849be79e99529a88371dff60c60aab424c077007f6979b4812 size: 524
```

```
$ docker image remove 127.0.0.1:5000/hello-world
Untagged: 127.0.0.1:5000/hello-world:latest
Untagged: 127.0.0.1:5000/hello-world@sha256:1a6fd470b9ce10849be79e99529a88371dff60c60aab424c077007f6979b4812
```
Use ```docker image ls``` to check the image ```127.0.0.1:5000/hello-world``` has been removed.
```
$ docker pull 127.0.0.1:5000/hello-world
Using default tag: latest
latest: Pulling from hello-world
Digest: sha256:1a6fd470b9ce10849be79e99529a88371dff60c60aab424c077007f6979b4812
Status: Downloaded newer image for 127.0.0.1:5000/hello-world:latest
```
