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
docker-machine create --driver virtualbox --virtualbox-memory "512" --virtualbox-disk-size "5000" minion1
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/docker1.png)
### Setting memory and hardisk
- setting memory
```bash
--virtualbox-memory "512"
```
pada script diatas digunakan untuk mengalokasikan memory menjadi 512mb

- setting hardisk
```bash
--virtualbox-disk-size "5000"
```
pada script diatas digunakan untuk mengalokasikan hardisk yang akan digunakan sebesar 5000mb

### Looking docker-machine
```bash
docker-machine ls
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/docker2.png)

### Looking ip manager
```bash
docker-machine ip minion1
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/docker3.png)

### Remote manager
```bash
docker-machine ssh minion1
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/docker4.png)

### Looking token manager
```bash
docker swarm init --advertise-addr 192.168.99.100
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/docker5.png)

### The minion joined a swarm as a worker
```bash
docker swarm join \
     --token SWMTKN-1-3q0upnmgp7ostlagikllmftajwwq8wpgxr1ec76jjfk91z4liy-eiopwwfaq0hpx8almxbkh27qz \
     192.168.99.100:2377
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/docker6.png)
### Looking status swarm
```bash
docker node ls
```
![alt tag](https://raw.githubusercontent.com/amanuDigm/TCCL_Docker-swarm/master/screenshots/docker7.png)
