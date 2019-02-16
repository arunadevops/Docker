docker-compose with nginx and mysql
Step 1
======
create directory new-comp
move into directory new-comp

step 2
docker-compose.yml
=================
version: '3'
services:
  databases:
    image: mysql
    ports:
    - "3306:3306"
    environment:
    - MYSQL_ROOT_PASSWORD=admin
    - MYSQL_USER=user
    - MYSQL_PASSWORD=password
    - MYSQL_DATABASE=demodb
  web:
     image: nginx
   
step 3
======
docker-compose up
Let the docker daemon be running

step 4
=======
Open up another Docker terminal
docker ps -a
Refer the database running - Note the container name.

Step 5
=======
docker exec -it newdckcomp_databases_1 bash
#mysql -u root - p
(admin is the password entered in the compose file)
# show databases;
# use demodb;
# show tables;
# exit;

Step 6
docker-compose down
docker-compose rm
