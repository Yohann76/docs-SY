Linux
===================

Commande Généraliste  
-------------------
Etre en “root” : sudo su 
lister les dossiers : ls
entrer dans un dossier : cd xxx
retour dans le dossier précédent  : cd ..
Supprimer un dossier : sudo rmdir xxx
supprimer un fichier : sudo rm xxx
Supprimer un répertoire plein : rm -Rf xxx
lire le contenu d'un fichier texte : cat
donner une autorisation à un fichier : sudo chmod 777 php.ini ou dev/log
Faire du SSH : ssh dev@127.0.0.1 -p 2222 ( accès SSH ) 
Lancer un .sh : sh start_moonlander2.sh

Edition de fichier 
-------------------
( nano ) : nano <fichier>( ctrl O + ctrl X pour sauver et quitter ) 
( vim) : vim<fichier>( I pour INSERT, ECHAP puis :wq)

Telecharger un archive avec un lien : wget ( wget <lien>  ) ( apt-get install wget ) 
Décompresser une archive a un endroit :  tar -C / usr / local -xzf nom_complet archive
Mettre à jour le système : sudo apt update && sudo apt upgrade
changer la version d’un package : 
sudo apt-get remove <paquet> && sudo apt-get install <paquet> -V <version>
Regarder ce qui utilise un port : sudo lsof -i:80

spécificité de Manjaro
-------------------
Synchroniser les dépots : $sudo pacman -Syy
Maj : $sudo pacman -Syu
Installer un paquet : $sudo pacman -S composer
installer une surcouche à octopi  : $sudo pacman -S trizen ( permet d’avoir des librairie privé ) 

spécificité de DietPi ( Voir ici )
-------------------

Voir en général le lancement : dietpi-launcher
Voir les config : dietpi-config
optimiser software : dietpi-software
Run the update : dietpi-update
voir les ressource moniteur : htop
Voir le cpu : cpu 



Outils de sécurité
-------------------
Se protéger 
ajouter un user “admin” : adduser rp
administrer les droit root a “admin : apt install sudo puis usermod -G root,sudo,adm rp
interdir la connexion root (etc/ssh/sshd_config): PermitRootLogin no
Finaliser : service ssh restart
installer un firewall strict : apt-get install iptables



Scanner un réseau
-------------------

Metasploit
-------------------
Nmap
-------------------
Information sur une IP : nmap 192.168.1.1

Ip sur  réseau avec le nom :  nmap -sL 192.168.1.1/24
Scanner une machine : nmap -A 192.168.1.45



Installation serveur web 
Un serveur web est un système capable de supporter des sites web de tout types avec des technologie différentes. 
technologie appréciée : PHP/SQL/Apache/phpmyadmin/Xdebug/ACL/Composer/zip/unzip/Git/php-intl/php-fpm/php-cli/php-xml/php-curl

réinitialiser mots de passe mysql : mysql -u root -p mysql

Regarder les logs Nginx : systemctl status nginx.service

Créer un user SQL et transférer ses droits :
CREATE USER 'user1'@'localhost' IDENTIFIED BY '000000';
GRANT ALL PRIVILEGES ON * . * TO 'user1'@'localhost';
FLUSH PRIVILEGES;

man in the middle attack SSH problem: 
; remove key if there are a middle man attack
;ssh-keygen -f "/root/.ssh/known_hosts" -R "164.132.105.114"
; or command: export ANSIBLE_HOST_KEY_CHECKING=False on 2 machine


Création web : 
-------------------

installer easy engine :wget -qO ee rt.cx/ee && sudo bash ee
creer un site : ee site create example.com --php7 --mysql
avoir une structure Wordpress : ee site update exemple.com --wp

Probléme clé SSH : 
ssh-keygen -R IpduServer 
Se connecter sur la machine voulu 


Tache Cron : 
-------------------

Script .SH : 
-------------------



