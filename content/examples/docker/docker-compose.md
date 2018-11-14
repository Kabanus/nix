##### ! filename - docker-compose.yml
version: '2'  

services:  

mysql:  
    image: mariadb:latest  
    restart: always  
    volumes:  
        - /database:/var/lib/mysql  
    ports:  
        - "127.0.0.1:3306:3306"  
    environment:  
        MYSQL_ROOT_PASSWORD: password  
    links:  
        - php
php:  
    image: php:7.2-fpm  
    build: .
