## The USER instruction sets the default user for the image to node. By default Docker runs containers as the root user
## The RUN mkdir -p /home/node/app instruction creates a directory called app inside the home directory of the node user. The home directory for any non-root user in Linux is usually /home/user-name by default.

## docker image build --file Dockerfile.dev --tag hello-dock:dev .
## docker container run --rm --detach --publish 3000:3000 --name hello-dock-dev hello-dock:dev

# bind mount
## docker container run --rm --publish 3000:3000 --name hello-dock-dev --volume D:\Docker-Practice\hello-dock-containerizing:/home/node/app hello-dock:dev
missing vite vì vite là package, mà trên local hiện tại ko có
## docker container run --rm --detach --publish 3000:3000 --name hello-dock-dev --volume D:\Docker-Practice\hello-dock-containerizing:/home/node/app --volume /home/node/app/node_modules hello-dock:dev

dùng Anonymous Volumes cho node_modules: share node_modules trong container


# production
## Use node image as the base and build the application.
## Copy the files created using the node image to an nginx image.
## Create the final image based on nginx and discard all node related stuff.

## docker image build --tag hello-dock:prod .
## docker container run --rm --detach --name hello-dock-prod --publish 8080:80 hello-dock:prod