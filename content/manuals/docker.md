### start image interactive shell
> docker run -it *image* **bash**

### start image background
> docker run -d *image*

##### keys
--publish *"ip:local port:container port"* // --publish "127.0.0.1:8080:80"  
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
> docker logs *container*

### remove all stopped containers
> docker rm -v ${docker ps -aq -f status=exited}

# make image from container
docker commit *container* **repository/image**
docker push **repository/image**