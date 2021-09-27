## Docker

[docker docs](https://docs.docker.com/)
[docker hub](https://hub.docker.com/)

## Commande Général  :

    $ docker --version // si docker est installé
    $ docker images// Répertoriez toutes les images du docker
    $ docker pull httpd // extraire l'image du docker hub
    $ docker run -it -d httpd // Cette commande créera un conteneur docker dans lequel le serveur HTTP Apache s'exécutera.
    $ docker ps // répertorie tous les conteneurs Docker exécutés avec les détails du conteneur.
    $ docker ps -a // Répertoriez tous les conteneurs Docker en cours d'exécution / sortis / arrêtés avec les détails du conteneur.
    $ docker exec -it 09ca6feb6efc bash // Accédez au conteneur Docker et exécuter des commandes à l'intérieur du conteneur.
    $ docker rm 9b6343d3b5a0 // remove container
    $ docker restart 09ca6feb6efc // redémarer un container
    $ docker stop 09ca6feb6efc // Stop un container
    $ docker start 09ca6feb6efc // start un container
    $ docker info // info docker, nbr image, version noyau...
    $ docker network ls // répertorie les détails de tout le réseau du cluster.
    $ docker login // connexion hub docker
    $ sudo docker cp 09ca6feb6efc:/usr/local/apache2/logs/httpd.pid /home/geekflare/  // Copiez un fichier d'un conteneur Docker vers le système local.

## Lancer docker :

Lancer docker s’il n’est pas lancer :docker-machine start default
tester docker :

    $ docker run hello world

    $ docker run -d -p 8080:80 nginx // Lancer serveur nginx sur port 80
    $ docker pull hello-world // récupérer une image du hub docker
    $ docker stop ID_RETOURNÉ_LORS_DU_DOCKER_RUN // stopper un conteneur
    $ docker build -t NomADonner // construire le DockerFile
    $ docker run -d -p 2368:2368 NomDonnerPrecedemment. // Exécuter l’environnement

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

    $ docker-compose up -d --build

## ORDRE POUR METTRE EN PLACE UNE CONFIG ( à partir des fichier )

    $ docker system prune ( remise a zero de docker ( perte de donnée ) )
    $ docker-compose down ( ferme les services et conteneurs )
    $ docker build -f docker/php/Dockerfile . -t  sfserver  ( nom libre ) ( créer une image )
    $ docker-compose up -d
    $ docker run -d -p 8080:80 sfserver  ( port pour nginx )

Adresse disponible pour Yohann : http://192.168.99.100:8000/
Adresse disponible pour PhpMyAdmin : http://192.168.99.100:8080/

A partir d’une config, docker-compose build && docker-compose up -d suffit à faire tourner les container. Si ne marche pas, aller à la section nettoyage

## NETTOYAGE


Arrêter et supprimer tous  les conteneurs :

    $ docker stop $(docker ps -a -q); docker rm $(docker ps -a -q)
    $ docker volume rm $(docker volume ls -qf dangling=true)

supprimer un conteneur :

    $ docker rm ‘id’

supprimer une image :

    $ docker rmi ‘id’  ( -f pour force )

supprimer l’ensemble des ressources :

    $ docker system prune

supprimer toutes les images :

    $ docker rmi $(docker images)

## INFORMATION

lister les conteneurs existant : docker ps
voir les image local présente : docker images -a

LANCER DES COMMANDES SYMFONY DANS DOCKER
Accès à la machine dans php, rentrer pour exécuter des commande - exit pour sortir


    $ docker exec -it php sh ( une fois avec var/www/projet #php bin/console..)

Accès à la machine pour exécuter des commande coup par coup

    $ docker-compose exec php bin/console …

## DEBUGGAGE :

cannot start service caused process_linux… : regarder les ligne de volumes ( voir -v )
ports allocated : changer le port d’utilisation du service
savoir qui écoute le port : sudo fuser 8080/tcp ( en -shell )
Couldn't connect to Docker daemon. You might need to start Docker for Windows.  ????????????????

Si la machine default plante :

    $ docker-machine rm default  ( supprimer la machine )
    $ docker-machine create --driver virtualbox default ( créer une machine default )
    $ docker-machine env default ( voir les variables )
    $ docker-compose build && docker-compose up -d

Ou Si :  Couldn't connect to Docker daemon - you might need to run `docker-machine start default`.

    $ docker-machine start default
    $ docker-machine env ( X2 )
    $ docker-machine start default
    $ docker-compose up -d

ANNEXE:
##

    $ docker-compose up --build
    $ démarrer un conteneur nginx $ docker run --name mynginx -P -d nginx
    $ docker exec -it ‘id’ bash
    $ docker-machine start default // Lancer la machine
    Se connecter avec le docker hub : docker login
    Donner les droits au daemon : sudo usermod -aG docker yohann ( nom séssion je pense )
    down les volumes : docker-compose down --volumes
    forcer à recréer : docker-compose up -d --build --force-recreate
    Rentrer dans un container  : docker exec -it nginx bash
    Virer cache : docker system prune --no-cache
    $ docker-compose logs app // Voir les logs du lancement

## Terminale ToolBox Docker :

projet : cd /c/wamp64/www/OC/BileMo_B2B_API (dev)
DOCKER SUR DEBIAN ( windows environment )  :

Doc install docker on debian : Docker On Debian

Installer docker :

    $ sudo apt-get install docker

Accéder au projet :

    $ cd /mnt/c/Users/yohan/OneDrive/desktop  ( Sacha )
    $ cd /mnt/c/wamp64/www/OC/BileMo_B2B_API ( Yohann )

Lancer docker :

    $ sudo service docker start

Lancer la config :

    $ docker-compose down
    $ docker-compose up -d

## Probléme Résolue :

probleme :

  Couldn't connect to Docker daemon at http+docker://localhost - is it running?

- Essayer en sudo
