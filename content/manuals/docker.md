##### start image interactive shell
> docker run -it *image* **bash**

##### start image background
> docker run -d *image*

###### options
--publish "127.0.0.1:8080:80" // port forwarding  
--hostname server_name // host name  
--name container_name // container name  
--env MYSQL_ROOT_PASSWORD=password // variables  
--link dependent_container:alias // dependencies  
--volume /data // mount

##### connect container interactive shell
> docker exec -it *container* **bash**

##### image list
> docker images  
> docker image list

##### container list
> docker ps // running  
> docker ps -a // all

##### container detail
> docker inspect *container*

##### container changes
> docker diff *container*

##### container events
> docker logs *container*

##### remove all stopped containers
> docker rm -v ${docker ps -aq -f status=exited}

##### make image from container
> docker commit *container* **repository/image**

##### push image to github
> docker push **repository/image**

##### build image
> docker build -t **repository/image**
