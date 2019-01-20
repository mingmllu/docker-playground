# Docker is changing IT landscape!

### Install Docker on Ubuntu 16.04

https://hub.docker.com/search?q=&type=edition&offering=community
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04

### Use Docker

[Learn Docker & Containers using Interactive Browser-Based Scenarios](https://www.katacoda.com/courses/docker)

#### Get a Docker container's IP address from the host

```
$ docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' XXXXXXXXXX
```
where ```XXXXXXXXXX``` is container name or container id

#### ----

```
$ docker container run --publish 80:80 --name webhost --detach nginx
```

```
$ docker pull mongo

$ docker container run --name mongo -d <image_name>
```

```
$ docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=true -v maysql-db:/var/lib/mysql mysql
```
Run ```docker volume ls```, you can see a new volume ```maysql-db``` has been created. You can inspect the volume:
```
$ docker volume inspect maysql-db
[
    {
        "CreatedAt": "2018-12-24T09:39:13-05:00",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/lib/docker/volumes/maysql-db/_data",
        "Name": "maysql-db",
        "Options": null,
        "Scope": "local"
    }
]
```
As a super suer, you can see a director ```/var/lib/docker/volumes/maysql-db/_data``` in the host machine.
You can create a volume ahead of running a container ```docker container run ...```, but usually you don't need to do this way for local development.

#### Persistent Data - Bind Mounting

Map a host file or directory to container file or directory.
Can't be used in dockerfile, you must do it at ```docker container run```

Bind your current working directory to a container directory:
```
$ docker container run -d --name nginx-mmlu -p 80:80 -v $(pwd):/usr/share/nginx/html nginx
```
Run the command ```bash``` in the running container ```nginx-mmlu```:
```
$ docker container exec -it nginx-mmlu bash
root@32f87f0fc375:/#
root@32f87f0fc375:/# cd /usr/share/nginx/html
root@32f87f0fc375:/usr/share/nginx/html# ls -l
(Here you will see the contents in your host working directory)
```

### docker-compose CLI
Not a product-grade tool, but ideal for local development and test

### Local private registry

