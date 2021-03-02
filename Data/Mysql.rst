.. index::
   single: Mysql; Show


Mysql
===================

`Mysql Doc`_

Show
-------------------
Voir la liste des database
::

    $ mysql> show databases;

changer un mot de passe d'un user:
::

   UPDATE mysql.user SET password=PASSWORD("wikipass") where User="zabbix";
   

changer le type de mot de passe :
::

   ALTER USER 'zabbix'@'ip_address' IDENTIFIED WITH mysql_native_password BY 'wikipass';
   

Selectionner une database
::

     $ mysql> use name_database

La liste des tables dans cette database
::

     $ mysql> show tables;

Afficher la les types des champs
::

     $ mysql> describe tablename;

Afficher la taille des base de données
::

     $ mysql> SELECT table_schema "Databases", sum( data_length + index_length) / 1024 / 1024 "Size of DB in MB" FROM information_schema.TABLES GROUP BY table_schema;

Requêtes
-------------------

SELECT :
::

     $ SELECT * FROM xxxx

UPDATE :
::

     $ UPDATE table SET nom_colonne = 'valeur'

DELETE :
::

     $ DELETE FROM table

Les commandes précedentes peuvent être suivi d'une clause WHERE pour préciser une condition.


Construction Base de données en Sql
-------------------

Création
::

     $ mysql> create database databasename;

Supprimer une base de données
::

     $ mysql> drop database databasename;

Suppression d’une table
::

     $ mysql> drop table tablename;

Création user
-------------------

Créer un user SQL et transférer ses droits :
::

   CREATE USER 'user1'@'localhost' IDENTIFIED BY '000000';
   GRANT ALL PRIVILEGES ON * . * TO 'user1'@'localhost';
   FLUSH PRIVILEGES;

Connexion
::

     $ mysql -u root -p
     $ mysql -h localhost -u root -p // connexion en tant que root password = root

( détails de la commande de connexion )

localhost : nom de votre serveur mysql
u : user souhaité, ici root
p : signifie qu'il vas falloir entrer le pass de l'utilisateur

Créer users
::

     $ mysql> CREATE USER 'users'@'localhost' IDENTIFIED BY 'mdp';

Donner les droits
::

     $ mysql> GRANT ALL PRIVILEGES ON * . * TO 'users'@'localhost';

Pour que les droits prennent effet
::

     $ mysql> FLUSH PRIVILEGES;

Listes des users
::

     $ mysql> select * from mysql.user;


Sauvegarde et restauration
-------------------

Sauvegarder une seule base de donnée, données et structure
::

     $ mysqldump -u username -p --databases databasename > databasename.sql

Sauvegarder toutes les bases, données et structure, dans un seul fichier .sql
::

     $ mysqldump -uroot -p --all-databases > alldatabases.sql

Restaurer une base à partir d'un fichier .sql contenant une sauvegarde de la base
::

     $ mysql -u username -p databasename < databasename.sql

Restaurer une base à partir d'un fichier. sql contenant une sauvegarde de toutes les bases
::

     $ mysql -u username -p --one-database mybase < alldatabases.sql



.. _`Mysql Doc`: https://dev.mysql.com/doc/
