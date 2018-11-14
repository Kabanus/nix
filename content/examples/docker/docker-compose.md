##### ! filename - docker-compose.yml
version: '2'

services:

  nginx:
    image: nginx:latest
    volumes:
      - /app/itm/content/wordpress:/var/www/wordpress
      - /app/itm/content/nginx/wordpress.conf:/etc/nginx/conf.d/default.conf
    ports:
      - "80:80"
    links:
      - php
      - mysql 

  php:
    image: php:7.2-fpm
    build: ./php
    volumes:
      - /app/itm/content/wordpress:/var/www/wordpress

  mysql:
    image: mariadb:latest
    volumes:
      - /app/itm/content/mysql:/var/lib/mysql
    ports:
      - "127.0.0.1:3306:3306"
    environment:
      MYSQL_ROOT_PASSWORD: password
