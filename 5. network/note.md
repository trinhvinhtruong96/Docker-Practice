## docker network ls

### bridge - The default networking driver in Docker. This can be used when multiple containers are running in standard mode and need to communicate with each other.

### host - Removes the network isolation completely. Any container running under a host network is basically attached to the network of the host system.

### none - This driver disables networking for containers altogether. I haven't found any use-case for this yet.

### overlay - This is used for connecting multiple Docker daemons across computers and is out of the scope of this book.

### macvlan - Allows assignment of MAC addresses to containers, making them function like physical devices in a network.