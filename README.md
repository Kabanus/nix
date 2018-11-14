# Docker

### start image interactive shell
> docker run -it *image* **bash**

### start image background
> docker run -d *image*

##### keys
--publish *"local port:container port"* // --publish "8080:80"  
--hostname *hostname* // --hostname newserver  
--name *container* // --name newcontainer  

### connect container interactive shell
> docker exec -it *container* **bash**

### image list
> docker images
> docker image list

### container list
> docker ps // running
> docker ps -a // all

### container detail
> docker inspect *container*

### container changes
> docker diff *container*

### container events
docker logs CONTAINER

### remove all stopped containers
docker rm -v ${docker ps -aq -f status=exited}

# make IMAGE from CONTAINER
docker commit CONTAINER REPOSITORY/NAME
docker push REPOSITORY/NAME
