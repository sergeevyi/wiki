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
