Outils de déploiement


Processus de déploiement Symfony	1
Docker	2
Commande Général  :	2
DOCKER-COMPOSE ET  DOSSIER “DOCKER” :	2
ORDRE POUR METTRE EN PLACE UNE CONFIG ( à partir des fichier )	2
NETTOYAGE	3
INFORMATION	3
LANCER DES COMMANDES SYMFONY DANS DOCKER	3
DEBUGGAGE :	3
ANNEXE:	4
DOCKER SUR DEBIAN ( windows environment )  :	4
Ansible :	5
COMMANDE GÉNÉRALE	5
HOSTING	5
PLAYBOOK	5
DEBUGGAGE :	6
Ancistrano ( construit sur Base de Ansible ) :	6
Intégration continu	6
CircleCi	6
SymfonyCloud	6
Github Action	6
Intégration continue avec ansible	6

Processus de déploiement Symfony

Déployer: 
Utiliser un fichier playbook.yaml
S’assurer de la bonne connexion a MySQL
Utiliser les bonne versions de PHP

processus pour sécuriser le déploiement: 
utiliser composer install --no-dev --optimize-autoloader
s’assurer que le composant Dotenv est présent sur la configuration de prod
s’assurer que le default.conf est supprimer de var/www
Docker
Commande Général  :

Lancer docker s’il n’est pas lancer :docker-machine start default
tester docker : docker run hello world  
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
$ docker-compose up -d --build 

ORDRE POUR METTRE EN PLACE UNE CONFIG ( à partir des fichier ) 
docker system prune ( remise a zero de docker ( perte de donnée ) )
docker-compose down ( ferme les services et conteneurs ) 
docker build -f docker/php/Dockerfile . -t  sfserver  ( nom libre ) ( créer une image ) 
docker-compose up -d
docker run -d -p 8080:80 sfserver  ( port pour nginx )

Adresse disponible pour Yohann : http://192.168.99.100:8000/
Adresse disponible pour PhpMyAdmin : http://192.168.99.100:8080/

A partir d’une config, docker-compose build && docker-compose up -d suffit à faire tourner les container. Si ne marche pas, aller à la section nettoyage



NETTOYAGE

Arrêter et supprimer tous  les conteneurs : docker stop $(docker ps -a -q); docker rm $(docker ps -a -q)
docker volume rm $(docker volume ls -qf dangling=true)
supprimer un conteneur : docker rm ‘id’ 
supprimer une image : docker rmi ‘id’  ( -f pour force ) 
supprimer l’ensemble des ressources : docker system prune
supprimer toutes les images : docker rmi $(docker images)

INFORMATION 
lister les conteneurs existant : docker ps 
voir les image local présente : docker images -a

LANCER DES COMMANDES SYMFONY DANS DOCKER
Accès à la machine dans php, rentrer pour exécuter des commande - exit pour sortir
$docker exec -it php sh ( une fois avec var/www/projet #php bin/console..)

Accès à la machine pour exécuter des commande coup par coup 
docker-compose exec php bin/console … 



DEBUGGAGE :
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
projet : cd /c/wamp64/www/OC/BileMo_B2B_API (dev)
DOCKER SUR DEBIAN ( windows environment )  :

Doc install docker on debian : Docker On Debian
Installer docker : sudo apt-get install docker
Accéder au projet :  
cd /mnt/c/Users/yohan/OneDrive/desktop  ( Sacha ) 
cd /mnt/c/wamp64/www/OC/BileMo_B2B_API ( Yohann ) 

Lancer docker : sudo service docker start 
Lancer la config : 
docker-compose down 
docker-compose up -d


Probléme Résolue : docker-compose command not found : Lien stackOverflow


Ansible : 
COMMANDE GÉNÉRALE
ansible localhost -m command -a "/bin/echo 'Hello Ansible'"
ansible localhost -m ping
ansible localhost -m composer -a "working_dir=./ no_dev=false"

HOSTING 

créer un host : créer un fichier /ansible/hosts.ini ( base ci-dessous) 
;--------------- ( IpV4 ) 
[local]
	127.0.0.1
	ansible_connection=local
[aws]  
15.188.106.233 ansible_user=ubuntu ansible_ssh_private_key_file=Yohann-EC2.pem
;---------------
ping sur un host :
 ansible 127.0.0.1 -m ping -i ansible/hosts.ini
Lister host(server) : 
ansible local --list-hosts -i ansible/hosts.ini



PLAYBOOK

IMPORTANT
exécuter le playbook : 
ansible-playbook ansible/playbook.yml -i ansible/hosts.ini

 exécuter le playbook avec le vault :
ansible-playbook ansible/playbook.yml -i ansible/hosts.ini --ask-vault-pass

Recréer les variables vault :
ansible-vault rekey foo.yml





DEBUGGAGE : 

deployment avec Nginx, si problème de 403 forbidden, voir/supprimer le défaut dans /etc/nginx/sites-enabled 
Faire un composer install manuellement par SSH 
	

Ancistrano ( construit sur Base de Ansible ) :
			A Voir plus tard 
Intégration continu
CircleCi
SymfonyCloud
Github Action

Intégration continue avec ansible
