##### docker install
- https://docs.docker.com/engine/install/   
- https://docs.docker.com/engine/install/linux-postinstall/   
- https://docs.docker.com/compose/install/   
> sudo usermod -aG docker $USER

##### cheat sheet
- https://www.docker.com/sites/default/files/d8/2019-09/docker-cheat-sheet.pdf   
- https://github.com/wsargent/docker-cheat-sheet   
- https://design.jboss.org/redhatdeveloper/marketing/docker_cheatsheet/cheatsheet/images/docker_cheatsheet_r3v2.pdf   
- https://gist.github.com/jonlabelle/bd667a97666ecda7bbc4f1cc9446d43a   
- https://github.com/sematext/cheatsheets/blob/master/docker-swarm-cheatsheet.md

##### k8s in docker
- https://kind.sigs.k8s.io/   

##### pull image
> docker pull **_image_**

##### start image cmd run
> docker run ubuntu echo "Hello, Kitty :)"   

##### start image interactive shell
> docker run -it **_image_** **/bin/bash**

##### start image background
> docker run -d **_image_**   
> docker run -d -p 80:80 -v $PWD/html:/usr/share/nginx/html nginx   

###### docker run options
- --detach // run container in backgroung   
- --interactive // keep STDIN open   
- --tty // pseudo-TTY   
- --publish *"127.0.0.1:8080:80"* // port forwarding  
- --publish-all // port forwarding (all)   
- --hostname *server_name* // host name  
- --name *container_name* // container name  
- --env *MYSQL_ROOT_PASSWORD=password* // variables  
- --link *container:alias* // dependencies  
- --volume */data* // mount   
- --rm // remove container when exit   
- --memory bytes // mem limit

##### show network info
> docker network inspect bridge   

##### volumes
> docker volume **command**

##### connect container interactive shell
> docker exec -it **_container_** **bash**

##### image list
> docker images  
> docker image list

##### container list
> docker ps // running  
> docker ps -a // all

##### container control
> docker start/stop/restart **_container_**   

##### container attach
> docker attach **_container_**   

##### container top
> docker top **_container_**   

##### container detail
> docker inspect **_container_**

##### container changes
> docker diff **_container_**

##### container events
> docker logs **_container_**

##### image history
> docker history **_image_**

##### remove all stopped containers
> docker rm -v $(docker ps -aq -f status=exited)

##### make image from container
> docker commit **_container_** **repository/image**

##### push image to github
> docker push **repository/image**

##### build image
> docker build -t **repository/image**

##### copy files
> docker cp **_container:/src_** **_dst_**   
> docker cp **_src_** **_container:/dst_**

##### docker swarm
> docker swarm init // init cluster   
> docker swarm join **_TOKEN_** // join cluster   
> docker swarm join-token (worker|manager) // get token   
