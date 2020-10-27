##### docker install
- https://docs.docker.com/engine/install/ubuntu/   
- https://docs.docker.com/engine/install/linux-postinstall/   
> sudo usermod -aG docker $USER

##### pull image
> docker pull **_image_**

##### show network info
> docker network inspect bridge   

##### start image cmd run
> docker run ubuntu echo "Hello, Kitty :)"   

##### start image interactive shell
> docker run -it **_image_** **/bin/bash**

##### start image background
> docker run -d **_image_**

##### volumes
> docker volume **COMMAND**

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
