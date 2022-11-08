# a dockerfile
A Dockerfile is a collection of instructions that, once processed by the daemon, results in an image
## FROM : base image
## EXPOSE: indicate the port that needs to be published 
## RUN: the command to execute in container shell
## CMD: default command for your image
## COPY: COPY local:container (copy from local)
## ADD: copy file to docker image (copy from internet)

## build image: docker image build .
after build image it return id, so we can use this id to run container 
