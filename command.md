# docker object command options
docker container run image-name

### Option: --publish host-port:container-port
Publish port for the container <br>
docker container run **--publish 8080:80** fhsinchy/hello-dock

### Option: --detach or -d
Keep container running in detach mode (run in background not related to the terminal) <br>
docker container run **--detach** --publish 8080:80 fhsinchy/hello-dock

### Option: --remove
remove container when it stopped

### Option: -it
interact with container - open interactive terminal (bash)
-i: interactive
-t: --tty

## 1. List Container: container ls
List running container <br>
**docker container ls**
### Option: -all or -a
List all container <br>
**docker container ls --all**

## 2. Name Container: --name
name container <br>
docker container run --detach --publish 8888:80 **--name hello-dock-container** fhsinchy/hello-dock
### Rename container: docker container rename container-identifier new-name
rename container <br>
container-identifier can be the name or id <br>
**docker container rename gifted_sammet hello-dock-container-2**

## 3. Stop container
docker container stop hello-dock-container <br>
**docker container stop container-identifier**

## 4. Kill container
docker container kill hello-dock-container-2 <br>
**docker container kill container-identifier**

## 5. Restart container
docker container start hello-dock-container <br>
when container stop <br>
**docker container start container-identifier**
when container running
**docker container restart container-identifier**

## 6. Create container
docker container run name : Create container and run <br>
docker container create name : Create container and but nut run

## 7. Remove dangling containers (container stopped or killed)
**docker container rm container-identifier**

## 8. Execute commands inside container
docker run alpine uname -a <br>
docker container run --rm busybox sh -c "echo -n my-secret | base64

## 9. Bind mount (--volume)
bind host folder with container folder: change in one site affect the other <br>
docker container run --rm -v C:\Users\Hi-XV\Desktop\aaa:/zone fhsinchy/rmbyext pdf
**docker container run --rm -v $(pwd):/zone fhsinchy/rmbyext pdf** <br>
**--volume (local file system directory absolute path):(container file system directory absolute path):(read write access)**

The difference between a regular image and an executable one is that the entry-point for an executable image is set to a custom program instead of sh, in this case the rmbyext program. And as you've learned in the previous sub-section, anything you write after the image name in a container run command gets passed to the entry-point of the image. <br>

So in the end the docker container run --rm -v $(pwd):/zone fhsinchy/rmbyext pdf command translates to rmbyext pdf inside the container. Executable images are not that common in the wild but can be very useful in certain cases.

## 10. dockerfile
A Dockerfile is a collection of instructions that, once processed by the daemon, results in an image

## 11.build image: docker image build .
after build image it return id, so we can use this id to run container <br>
### tag image: --tag image-repository:image-tag 
docker image build --tag custom-nginx:packaged .

## 12. list, remove image: same as container
**docker image rm image-identifier** <br>
docker image rm custom-nginx:packaged
docker image prune --force: cleanup all un-tagged dangling images