Docker swarm
===

### install docker-machine
```bash
curl -L https://github.com/docker/machine/releases/download/v0.10.0/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine &&
    chmod +x /tmp/docker-machine &&
    sudo cp /tmp/docker-machine /usr/local/bin/docker-machine
```

### Create docker-machine
```bash
docker-machine create --driver virtualbox --virtualbox-memory "512" --virtualbox-disk-size "5000" node1
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/1.png)

### Setting memory and hardisk
- setting memory
```bash
--virtualbox-memory "512"
```
allocates 512MB memory

- setting hardisk
```bash
--virtualbox-disk-size "5000"
```
allocates 5000MB hardisk

### Looking docker-machine
```bash
docker-machine ls
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/docker2.png)

### Looking ip manager
```bash
ifconfig
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/2.png)

### Remote manager
```bash
docker-machine ssh node1
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/3.png)

### Looking token manager
```bash
docker swarm init --advertise-addr 192.168.99.1
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/2.2.png)

### The minion joined a swarm as a worker
```bash
docker swarm join \
    --token SWMTKN-1-34sz44qnbosozfm7j93dli2m4odcsl8f9zhdqmwrcqen3bewco-erlp1v07bdj1zq4pbrmccj7v8 \
    192.168.99.1:2377
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/4.png)

### Looking status swarm
```bash
docker node ls
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/5.png)

### Deploy service to Docker-Swarm
```bash
docker service create --name slims -p 8080:80 --replicas 2 amanu/slims_web:1.0
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/6.png)

  - Looking service
  ```bash
  docker service ls
  ```
  ![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/7.png)

### How to scale
```bash
docker service scale slims=8
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/8.png)

  - Looking service
  ```bash
  docker service ls
  ```
  ![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/9.png)
