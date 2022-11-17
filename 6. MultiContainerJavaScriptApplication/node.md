## Run Database
### docker container run --detach --name=notes-db --env POSTGRES_DB=notesdb --env POSTGRES_PASSWORD=secret --network=notes-api-network postgres:12
#### Run postgres db with env from the doc, with custom network to isolate from default network

## Named Volumes in Docker
### use name volume to persist data in a specific directory use by container, when container destroyed the data not lost
### docker volume create volume-name
#### docker volume create notes-db-data
### stop DB and restart with volume name
#### docker container stop notes-db
#### docker container rm notes-db
#### docker container run --detach --volume notes-db-data:/var/lib/postgresql/data --name=notes-db --env POSTGRES_DB=notesdb --env POSTGRES_PASSWORD=secret --network=notes-api-network postgres:12
#### docker container inspect --format='{{range .Mounts}} {{ .Name }} {{end}}' notes-db

## Access Logs from a Container in Docker
### docker container logs container-identifier
### docker container logs notes-db -f

## As you've learned in the previous section, the containers have to be attached to a user-defined bridge network in order to communicate with each other using container names
### docker network create notes-api-network
### docker network connect notes-api-network notes-db

## notes-api
### docker image build --tag notes-api .
### docker container inspect notes-db
#### make sure the database container is running, and is attached to the notes-api-network
#### docker container run --detach --name=notes-api --env DB_HOST=notes-db --env DB_DATABASE=notesdb --env DB_PASSWORD=secret --publish=3000:3000 --network=notes-api-network notes-api

## Execute Commands in a Running Container
### docker container exec container-identifier command
### docker container exec notes-api npm run db:migrate
### docker container exec -it notes-api sh

## Write Management Scripts in Docker
### learn later