## Mysql


[Mysql Doc](https://dev.mysql.com/doc/)

Commandes courante
-------------------

Voir la liste des database
::

    $ mysql> show databases; // list des database
    $ mysql> use name_database // Selectionner une database
    $ mysql> show tables; // La liste des tables dans cette database
    $ mysql> SELECT * FROM user; // voir le contenu de toute la table user


Gestion User
::

   UPDATE mysql.user SET password=PASSWORD("wikipass") where User="zabbix"; // change password
   UPDATE mysql.user SET passwd="wikipass" where User="zabbix"; // change password
   ALTER USER 'zabbix'@'ip_address' IDENTIFIED WITH mysql_native_password BY 'wikipass'; // changer le type de mot de passe
   FLUSH PRIVILEGES; // Sauvegarder les modifications en ligne de commande

Commande divers
-------------------
::

     $ mysql> describe tablename; // Afficher la les types des champs
     $ mysql> SELECT table_schema "Databases", sum( data_length + index_length) / 1024 / 1024 "Size of DB in MB" FROM information_schema.TABLES GROUP BY table_schema; // Afficher la taille des base de données

Requêtes
-------------------

SELECT :
::

     $ SELECT * FROM xxxx ;

UPDATE :
::

     $ UPDATE table SET nom_colonne = 'valeur' ;

DELETE :
::

     $ DELETE FROM table ;

Les commandes précedentes peuvent être suivi d'une clause WHERE pour préciser une condition.


Commande relative à la gestion de la bdd
-------------------
::


     $ mysql> create database databasename; // Création bdd
     $ mysql> drop database databasename; // Supprimer une base de données
     $ mysql> drop table tablename; // Suppression d’une table


Création user
-------------------
Créer un user SQL et transférer ses droits :
::

   CREATE USER 'user1'@'localhost' IDENTIFIED BY '000000'; // créer
   GRANT ALL PRIVILEGES ON * . * TO 'user1'@'localhost'; // donner les droit
   FLUSH PRIVILEGES; // pour faire prendre effet les droits

Connexion
::

     $ mysql -u root -p
     $ mysql -h localhost -u root -p // connexion en tant que root password = root

( détails de la commande de connexion )

localhost : nom de votre serveur mysql
u : user souhaité, ici root
p : signifie qu'il vas falloir entrer le pass de l'utilisateur


Listes des users
::

     $ mysql> select * from mysql.user;


Sauvegarde et restauration
-------------------
::

     $ mysqldump -u username -p --databases databasename > databasename.sql // Sauvegarder une seule base de donnée, données et structure
     $ mysqldump -uroot -p --all-databases > alldatabases.sql // Sauvegarder toutes les bases, données et structure, dans un seul fichier .sql
     $ mysql -u username -p databasename < databasename.sql // Restaurer une base à partir d'un fichier .sql contenant une sauvegarde de la base
     $ mysql -u username -p --one-database mybase < alldatabases.sql // Restaurer une base à partir d'un fichier. sql contenant une sauvegarde de toutes les bases
