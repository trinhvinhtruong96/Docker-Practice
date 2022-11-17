## Docker Compose Basics (docker-compose.yaml)
### refer to Dockerfile.dev
### line 10: we run npm install instead of npm run install --only=prod because we want the development dependencies also
### line 15: we set the NODE_ENV environment variable to development instead of production
### line 24: we use a tool called nodemon to get the hot-reload feature for the API
### Project has two containers
#### notes-db - A database server powered by PostgreSQL
#### notes-api - A REST API powered by Express.js
### db service
#### using the official PostgreSQL image
### api service 
#### user image from docker file
### build: source file to build image
### image: image name to be build
### volumes: define volumes
#### f you don't define a name, the volume will be named following the project-directory name_volume-key and the key here is notes-db-dev-data

## Start Services in Docker Compose
### docker-compose --file docker-compose.yaml up --detach

## Execute Commands Inside a Running Service in Docker Compose
### docker-compose exec service-name command
### docker-compose exec api npm run db:migrate
## Access Logs from a Running Service in Docker Compose
### docker-compose logs service-name
### docker-compose logs api -f
## How to Stop Services in Docker Compose
### docker-compose down --volumes
#### The --volumes option indicates that you want to remove any named volume(s) defined in the volumes block

## List Services in Docker Compose
### docker-compose ps