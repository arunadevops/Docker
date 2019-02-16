Simple docker-compose with redis and postgre
=============================================
Step 1:
=======
Create a directory new-comp1 
Move into directory new-comp1

Step 2

docker-compose.yml
==================
version: '3'
services:
  web:
    image: nginx
    depends_on:
      - db
      - redis
  redis:
    image: redis
  db:
    image: postgres

Step 2:
docker-compose up
Let the Daemon process be running
Step 3
Open up a new Docker Terminal... 

Docker ps- a
### execute the redis container into the shell with docker exec -it 
# redis-server
# redis-cli
# ping 
# CONFIG GET *
# exit
# exit

Step3
docker-compose down
docker-compose rm
