.. index::
   single: Docker; 

Docker
===================

`docker docs <https://docs.docker.com/>`_
`docker hub <https://hub.docker.com/>`_

Commande Général  :
-------------------

Lancer docker s’il n’est pas lancer :docker-machine start default
tester docker : 
::

    docker run hello world  

Lancer serveur nginx sur port 80 : docker run -d -p 8080:80 nginx
récupérer une image du hub docker : docker pull hello-world
stopper un conteneur : docker stop ID_RETOURNÉ_LORS_DU_DOCKER_RUN
construire le DockerFile : docker build -t NomADonner
Exécuter l’environnement : docker run -d -p 2368:2368 NomDonnerPrecedemment.
puis accéder au localhost créer avec le port du dockerFile : http://127.0.0.1:2368.
connaître son IP de machine virtuel : docker-machine ip default

push une image : docker push hasalex/img
executer un fichier docker-compose.yml : docker-compose up -d
DOCKER-COMPOSE ET  DOSSIER “DOCKER” :
Mettre en place les fichier 
docker-compose.yaml à la racine 
Dossier Docker à la racine 
Modifier/ajouté les variable d'environnement du .env si il y a 
Commande : 
::

    $ docker-compose up -d --build 

ORDRE POUR METTRE EN PLACE UNE CONFIG ( à partir des fichier )
-------------------
::

    docker system prune ( remise a zero de docker ( perte de donnée ) )
    docker-compose down ( ferme les services et conteneurs ) 
    docker build -f docker/php/Dockerfile . -t  sfserver  ( nom libre ) ( créer une image ) 
    docker-compose up -d
    docker run -d -p 8080:80 sfserver  ( port pour nginx )

Adresse disponible pour Yohann : http://192.168.99.100:8000/
Adresse disponible pour PhpMyAdmin : http://192.168.99.100:8080/

A partir d’une config, docker-compose build && docker-compose up -d suffit à faire tourner les container. Si ne marche pas, aller à la section nettoyage

NETTOYAGE
-------------------

Arrêter et supprimer tous  les conteneurs : 
::
    docker stop $(docker ps -a -q); docker rm $(docker ps -a -q)
    docker volume rm $(docker volume ls -qf dangling=true)

supprimer un conteneur :
::
    docker rm ‘id’ 

supprimer une image :
::
    docker rmi ‘id’  ( -f pour force ) 

supprimer l’ensemble des ressources :
::
    docker system prune

supprimer toutes les images :
::
    docker rmi $(docker images)

INFORMATION 
-------------------
lister les conteneurs existant : docker ps 
voir les image local présente : docker images -a

LANCER DES COMMANDES SYMFONY DANS DOCKER
Accès à la machine dans php, rentrer pour exécuter des commande - exit pour sortir
::

    $docker exec -it php sh ( une fois avec var/www/projet #php bin/console..)

Accès à la machine pour exécuter des commande coup par coup 
::

    docker-compose exec php bin/console … 


DEBUGGAGE :
-------------------
cannot start service caused process_linux… : regarder les ligne de volumes ( voir -v ) 
ports allocated : changer le port d’utilisation du service 
savoir qui écoute le port : sudo fuser 8080/tcp ( en -shell ) 
Couldn't connect to Docker daemon. You might need to start Docker for Windows.  ???????????????? 

Si la machine default plante :
::

    $ docker-machine rm default  ( supprimer la machine ) 
    $ docker-machine create --driver virtualbox default ( créer une machine default ) 
    $ docker-machine env default ( voir les variables ) 
    $ docker-compose build && docker-compose up -d

Ou Si :  Couldn't connect to Docker daemon - you might need to run `docker-machine start default`.
::

    $ docker-machine start default
    $ docker-machine env ( X2 ) 
    $ docker-machine start default
    $ docker-compose up -d 

ANNEXE: 
-------------------
docker-compose up --build  ( couteau suisse ) 
démarrer un conteneur nginx $ docker run --name mynginx -P -d nginx
docker exec -it ‘id’ bash 
Lancer la machine : docker-machine start default 
Se connecter avec le docker hub : docker login
Donner les droits au daemon : sudo usermod -aG docker yohann ( nom séssion je pense ) 
down les volumes : docker-compose down --volumes
forcer à recréer : docker-compose up -d --build --force-recreate
Rentrer dans un container  : docker exec -it nginx bash 
Virer cache : docker system prune --no-cache 


Terminale ToolBox Docker :
-------------------
projet : cd /c/wamp64/www/OC/BileMo_B2B_API (dev)
DOCKER SUR DEBIAN ( windows environment )  :

Doc install docker on debian : Docker On Debian
Installer docker :
::

    sudo apt-get install docker

Accéder au projet :  
cd /mnt/c/Users/yohan/OneDrive/desktop  ( Sacha ) 
cd /mnt/c/wamp64/www/OC/BileMo_B2B_API ( Yohann ) 

Lancer docker : sudo service docker start 
Lancer la config : 
::

    docker-compose down 
    docker-compose up -d


Probléme Résolue : docker-compose command not found : Lien stackOverflow


Configuration
##############



Configuration docker-compose fonctionnel:
-------------------------------------------


::
    version: '3.7'

    services:

    mysql:
        container_name: mysql
        environment:
        MYSQL_ROOT_PASSWORD: root #${MYSQL_ROOT_PASSWORD}
        image: mysql:5.7
        restart: always
        volumes:
        - db_data:/var/lib/mysql

    nginx:
        container_name: nginx
        image: nginx
        links:
        - php
        ports:
        - 8000:80 #${NGINX_PORT}:80
        restart: always
        volumes:
        - .:/var/www/Symfony-Snowtricks:cached #${SYMFONY_ROOT_DIR}:cached
        - ./docker/nginx/conf.d/default.conf:/etc/nginx/conf.d/default.conf
        working_dir: /var/www/Symfony-Snowtricks  #${SYMFONY_ROOT_DIR}

    php:
        build: docker/php
        container_name: php
        depends_on:
        - mysql

        ports:
        - 9000:9000 #${PHP_PORT}:9000
        restart: always
        volumes:
        - .:/var/www/Symfony-Snowtricks:cached #${SYMFONY_ROOT_DIR}:cached
        working_dir: /var/www/Symfony-Snowtricks #${SYMFONY_ROOT_DIR}

    phpmyadmin:
        image: phpmyadmin/phpmyadmin
        restart: always
        links:
        - mysql:mysql
        ports:
        - "8080:80"
        environment:
        PMA_HOST: mysql
        MYSQL_ROOT_PASSWORD: root

    volumes:
    db_data:

DockerFile PHP:
-------------------------------------------

::
    FROM    composer:1.8 as composer
    FROM    php:7.3-fpm-alpine

    COPY    --from=composer /usr/bin/composer /usr/local/bin/composer

    # Removing APKINDEX warnings
    RUN     rm -rf /var/cache/apk/* && \
            rm -rf /tmp/*
    RUN     apk update

    # Native libs and building dependencies
    # su-exec > gosu (10kb instead of 1.8MB)
    RUN     apk add --update --no-cache \
            git \
            unzip \
            make \
            nodejs \
            yarn \
            zlib-dev \
            libzip-dev \
            ca-certificates \
            php-intl \
            && apk add --no-cache --virtual .build-deps \
                $PHPIZE_DEPS \
                curl \
                icu-dev \
            && docker-php-ext-configure intl \
            && docker-php-ext-install \
                zip \
                intl \
                pdo_mysql \
            && yes | pecl install xdebug \
            && apk add --no-cache su-exec \
            && addgroup bar \
            && adduser -D -h /home -s /bin/sh -G bar foo \
            && apk del .build-deps

    # PHP config
    COPY    conf.d/php.ini /usr/local/etc/php
    COPY    conf.d/symfony.ini /usr/local/etc/php/conf.d

Nginx conf.d:
-------------------------------------------

:: 
    server {

        root /var/www/Symfony-Snowtricks/public;

        location / {
            try_files $uri /index.php$is_args$args;
        }
        # PROD
        location ~ ^/index\.php(/|$) {
            fastcgi_pass php:9000;
            fastcgi_split_path_info ^(.+\.php)(/.*)$;
            include fastcgi_params;
            fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
            fastcgi_param DOCUMENT_ROOT $realpath_root;
            internal;
    }
    location ~ \.php$ {
        return 404;
    }

    error_log /var/log/nginx/smartfact_prod_error.log;
    access_log /var/log/nginx/smartfact_prod_access.log;
    }