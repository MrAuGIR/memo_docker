# Docker compose

**liens utiles** :
https://yoandev.co/un-environnement-de-developpement-symfony-5-avec-docker-et-docker-compose

## Exemple de fichier docker-compose.yml
```
version: "3.8"
services:

    db:
        image: mysql
        container_name: db_docker_symfony
        restart: always
        volumes:
            - db-data:/var/lib/mysql
        environment:
            MYSQL_ALLOW_EMPTY_PASSWORD: 'yes'
        networks:
            - dev

    phpmyadmin:
        image: phpmyadmin
        container_name: phpmyadmin_docker_symfony
        restart: always
        depends_on:
            - db
        ports:
            - 8080:80
        environment:
            PMA_HOST: db
        networks:
            - dev

    maildev:
        image: maildev/maildev
        container_name: maildev_docker_symfony
        command: bin/maildev --web 80 --smtp 25 --hide-extensions STARTTLS
        ports:
          - "8081:80"
        restart: always
        networks:
            - dev

    www:
        build: php
        container_name: www_docker_symfony
        ports:
          - "8741:80"
        volumes:
            - ./php/vhosts:/etc/apache2/sites-enabled
            - ./:/var/www
        restart: always
        networks:
            - dev

networks:
    dev:

volumes:
    db-data:


```
## Commandes

1.
`` docker-compose up -d ``

2. creation d'un projet symfony dans le conteneur
`` docker exec www_docker_symfony composer create-project symfony/website-skeleton projectDockerSymfony ``

## liens a tester après le docker-compose up
* maildev
http://127.0.0.1:8081/#/

* phpmyadmin
http://127.0.0.1:8080/

* projet symfony

