# Docker

```
index.html
<!-- index.html -->
<html>

 <head>
   <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css" rel="stylesheet" integrity="sha256-MfvZlkHCEqatNoGiOXveE8FIwMzZg4W85qfrfIFBfYc= sha512-dTfge/zgoMYpP7QbHy4gWMEGsbsdZeCXz7irItjcC3sPUFtf0kuFbDz/ixG7ArTxmDjLXDmezHubeNikyKGVyQ==" crossorigin="anonymous">
   <title>Docker Quick Start</title>
 </head>

 <body>
```

```
$ docker run --name webserver -v $(pwd):/usr/share/nginx/html -d -p 8080:80 nginx
```

# Dockerfile

# Portainer

```
docker service create \
   --name portainer \
   --publish 9000:9000 \
   --constraint 'node.role == manager' \
   --mount type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock \
   portainer/portainer \
   -H unix:///var/run/docker.sock
```

# Swarm

Swarm demo:

```
docker-machine create --driver virtualbox manager
docker-machine create --driver virtualbox worker1
docker-machine create --driver virtualbox worker2
docker-machine create --driver virtualbox worker3
```

1. Create a Swarm Manage node

```
docker-machine ssh manager
docker swarm init --advertise-addr 192.168.99.100
```

2. Add one Docker Node to the Swarm cluster

```
docker-machine ssh worker1
docker swarm join --token SWMTKN-1-5bq9h5bwxnsv3kkz2i9qfc3ap0el6oeb0jgi6h7pcr5friuqeo-cdbuk4h9tgto95bsm40gnbypg 192.168.99.100:2377
docker-machine ssh worker2
docker swarm join --token SWMTKN-1-0868q4bgmq863klfau4cm1ki3nzwdzbtl3kzlizsjny314r4qk-6wvf5n2b4bpi8a5idjv5thwkn 192.168.99.100:2377
docker-machine ssh worker3
docker swarm join --token SWMTKN-1-0868q4bgmq863klfau4cm1ki3nzwdzbtl3kzlizsjny314r4qk-6wvf5n2b4bpi8a5idjv5thwkn 192.168.99.100:2377
```

3. Check nodes

```
docker-machine ssh manager
docker node ls
```

4. Create a service

```
docker service create --replicas 1 --name helloworld --publish 80:8000 jwilder/whoami
docker service ls
```

We use docker image jwilder/whoami which is a simple HTTP docker service that return it’s container ID. It will export port 8000 by default, we use --publish 80:8000 to publish its http port to 80.

```
curl 127.0.0.1
```

5. Scale a service
   Run the following command to change the desired state of the service running in the swarm:

```
$ docker service scale <SERVICE-ID>=<NUMBER-OF-TASKS>
```

For example:

```
$ docker service scale helloworld=5

helloworld scaled to 5
```
