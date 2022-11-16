## docker network ls

### bridge - The default networking driver in Docker. This can be used when multiple containers are running in standard mode and need to communicate with each other.

### host - Removes the network isolation completely. Any container running under a host network is basically attached to the network of the host system.

### none - This driver disables networking for containers altogether. I haven't found any use-case for this yet.

### overlay - This is used for connecting multiple Docker daemons across computers and is out of the scope of this book.

### macvlan - Allows assignment of MAC addresses to containers, making them function like physical devices in a network.

## Default bridge network
### Any container you run will be automatically attached to this bridge network
### Containers attached to the default bridge network can communicate with each others using IP addresses:
#### User-defined bridges provide automatic DNS resolution between containers: use container name as DNS
#### User-defined bridges provide better isolation
#### Containers can be attached and detached from user-defined networks on the fly
##### Keep in mind, though, that in order for the automatic DNS resolution to work you must assign custom names to the containers. Using the randomly generated name will not work.

## Create network
### docker network create network-name
## Attach container to network
### docker network connect network-identifier container-identifier
### docker container run container-identifier --network network-identifier

#### docker container run --network skynet --rm --name alpine-box -it alpine sh
##### ping hello-dock: ping hello-dock inside alpine-box create on the command below

## Detach container from network
### docker network disconnect network-identifier container-identifier

## Inspect network 
### docker network inspect --format='{{range .Containers}} {{.Name}} {{end}}' bridge

## Remove network
### docker network rm network-identifier