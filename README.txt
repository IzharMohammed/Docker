docker pull mongo --> to pull mongo image from image hub/image registry

docker run mongo --> to run mongo container on your machine/to start the image 

docker images --> to see all of the images in your local machine running currently

docker ps --> to see all containers that u r running

docker run -d mongo --> run it in background or run it in detached mode so that the terminal is free to run other commands

docker run -p 27017:27017 -d mongo --> to run mongo in specific port

docker kill CONTAINER_ID --> to kill a specific container 

docker rmi mongo --force --> to kill a mongo image

docker build -t (name what we want to give) . --> we can create our own image 
docker run -p 3000:3000 izhar --> now we can see our project on local host 3000

Env variables :- 
docker run -p 3000:3000 -e DATABASE_URL="" image_name

To Run in shell :-
docker exec -it CONTAINER_ID /bin/bash

Volumes :- 

Creation of volume :-
docker volume create volume_databaseName

To see all the volumes :-
docker volume ls

Mount the folder in mongo which actually stores the data to this volume (/data/db is where mongo stores the data in it) :-
docker run -v volume_database:/data/db -p 27017:27017 mongo

Creation of network :-
docker network create my_custom_network

To see all the networks :-
docker network ls

To see the contents in the image :- 
docker exec COTAINER_ID ls 




Project postgres docker :- 
compose.yaml file :- 
version : '3.9'

services :
  db :
    container_name: db
    image: postgres:12
    restart: always
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
      POSTGRES_DB: postgres
    ports:
      - 5432:5432
    volumes: 
      - pgdata:/var/lib/postgresql/data

volumes:
  pgdata: {}

docker compose build

command to run it :- 
docker compose up -d db (db is the name of the service , if i add another service then it changes to what the name of the service is)

cmd to go inside the postgres db :- 
docker exec -it db psql -U postgres (if there is db service in compose file)
docker exec -it CONTAINERID psql -U postgres
-U ==> username which allocated in compose.yaml file
\l
\dt



docker exec -it backend(its the name of the container) npx prisma migrate dev --name init

npx prisma studio --> to open prisma studio

npx create-next-app@latest --no-git  