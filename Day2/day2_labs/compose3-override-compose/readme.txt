Step 1
==========
New Directory new-comp2

Step 2
========
docker-compose.yml
web:
  image: nginx
  links:
    - db
    - cache
db:
  image: postgres
cache:
  image: redis

docker-compose up -d 

(See creation of the Containers...)

Step 3
docker-compose.override.yml
=========================
web:
  volumes:
    - ".:/code"
  ports:
    - "8883:80"
  environment:
    DEBUG: "true"

db:
  ports:
    - "5432:5432"
cache:
  ports:
    - "6379:6379"

### ImportantBefore running docker-compose 
docker-compose down
####- ensure the corresponding containers are stopped and pruned.
docker-compose rm
Step 4
=======
docker-compose up -d 

Step 5
=======
Check for ports in docker ps -a 
docker port <<name of container>>
Enter into docker exec -it of web shell and check for echo $DEBUG

docker-compose.prod.yml
========================
web:
  ports:
    - 80:80
  environment:
    PRODUCTION: "true"
cache:
  environment:
    TTL: "500"

Step 6
========
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d

Step 7
=======
execute into container of shell and check for $PRODUCTION

Step 8
=======
docker-compose down
docker-compose rm

docker-machine inspect default
docker-machine env default
