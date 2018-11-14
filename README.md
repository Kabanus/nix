# Docker

## start image interactive
> docker run -it **image** *bash*

### start image background
> docker run -d **image**

##### keys
--publish "local port:container port"
--hostname hostname
--name CONTAINER_NAME

# start CONTAINER interactive shell
docker exec -it CONTAINER bash

# image list
docker image list

# container list
docker ps // running
docker ps -a // all

# container detail
docker inspect CONTAINER

# container changes
docker diff CONTAINER

# container events
docker logs CONTAINER

# remove all stopped containers
docker rm -v ${docker ps -aq -f status=exited}

# make IMAGE from CONTAINER
docker commit CONTAINER REPOSITORY/NAME
docker push REPOSITORY/NAME
