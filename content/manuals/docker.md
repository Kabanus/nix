##### docker install
> https://docs.docker.com/engine/install/ubuntu/   
> sudo usermod -aG docker $USER

##### start image interactive shell
> docker run -it **_image_** **bash**

##### start image background
> docker run -d **_image_**

###### options
- --publish *"127.0.0.1:8080:80"* // port forwarding  
- --hostname *server_name* // host name  
- --name *container_name* // container name  
- --env *MYSQL_ROOT_PASSWORD=password* // variables  
- --link *container:alias* // dependencies  
- --volume */data* // mount

##### connect container interactive shell
> docker exec -it **_container_** **bash**

##### image list
> docker images  
> docker image list

##### container list
> docker ps // running  
> docker ps -a // all

##### container detail
> docker inspect **_container_**

##### container changes
> docker diff **_container_**

##### container events
> docker logs **_container_**

##### image history
> docker history **_image_**

##### remove all stopped containers
> docker rm -v ${docker ps -aq -f status=exited}

##### make image from container
> docker commit **_container_** **repository/image**

##### push image to github
> docker push **repository/image**

##### build image
> docker build -t **repository/image**
