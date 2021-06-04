.. index::
   single: Linux;

Linux
===================

Commande Généraliste
-------------------
::

   wget // ( wget <lien>  ) ( apt-get install wget )
   cat /etc/group | awk -F: '{print $ 1}' // lister les groupes utilisateurs
   cut -f1 -d: /etc/passwd // lister les utilisateurs
   userdel -r pierre // supprimer un user
   pkill -f nginx // supprimer un processus avec un nom
   lsof -i tcp:8080 // lister les processus sur le port ...
   nohup <maCommande> & // execute un programme en tache de fond
   sudo su // être en root tous le temps
   ls // lister les dossier
   cd // rentrer dans un dossier
   sudo rmdir NomDuFichier // supprimer un dossier
   Supprimer un répertoire plein : rm -Rf NomDuFichier // supprimer un repertoire
   cat // afficher le contenu d'un fichier
   pwd // afficher le repertoire courant
   sudo chmod 777 php.ini ou dev/log // donner une autorisation a un fichier
   ssh dev@127.0.0.1 -p 2222 // faire du SSH
   sh start_moonlander2.sh // lancer un .shell
   ./<nom_binaire> // lancer un binaire
   top // voir les processus en cours
   sudo kill <process_id> // kill un processus
   nano || vim // editer un fichier
   wget <lien> // telecharger une archive
   tar -C / usr / local -xzf nom_complet archive // Décompresser une archive a un endroit
   sudo apt update && sudo apt upgrade //Mettre à jour le système
   sudo apt-get remove <paquet> && sudo apt-get install <paquet> -V <version> // changer la version d’un package
   sudo lsof -i:80 // Regarder ce qui utilise un port
   nmap <ip> // avoir des info sur l'IP ( option -sL, A )
   mysql -u root -p mysql // se connecter a mysql
   systemctl status nginx.service // obtenir le status d'un service
   job // voir les taches de fond
   wget -qO ee rt.cx/ee && sudo bash ee && ee site create example.com --php7 --mysql // créer une structure php-sql basique
   Cp fichier 1 fichier2 // copier un fichier
   mv xxx xxx // deplacer un fichier
   ulimit -a // lister les limites d'une machine


Shell speciaux :
::

   CREATE USER 'user1'@'localhost' IDENTIFIED BY '000000';
   GRANT ALL PRIVILEGES ON * . * TO 'user1'@'localhost';
   FLUSH PRIVILEGES;


man in the middle attack SSH problem:
::

   ; remove key if there are a middle man attack
   ;ssh-keygen -f "/root/.ssh/known_hosts" -R "164.132.105.114"
   ; or command: export ANSIBLE_HOST_KEY_CHECKING=False on 2 machine


General :
-------------------

- ./.bashrc est le fichier de démarrage
- http://www.tux-planet.fr/empecher-la-suppression-dun-fichier-ou-dun-repertoire/#:~:text=Voici%20une%20astuce%20pour%20les,fichiers%20Ext2%2C%20Ext3%20et%20Ext4.




Tuto Projet Raspberry
-------------------
`Miner avec un futurebit`_

.. _`Miner avec un futurebit`: https://medium.com/@david_senate/running-a-super-low-cost-digibyte-scrypt-miner-rig-with-a-raspberry-pi-3-model-b-and-a-futurebit-14dd7d95e566
.. _`Autre lien DietPi config`: http://dietpi.com/phpbb/viewtopic.php?f=8&t=5#p5
.. _`Configuration DietPi`: http://blog.choum.ca/20170819-dietpi-configuration-de-base
.. _`Site DietPi`: https://dietpi.com/#noAction
