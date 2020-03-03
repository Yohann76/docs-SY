.. index::
   single: Mysql; Show

Mysql
===================
`Mysql Doc <https://dev.mysql.com/doc/>`_

Show
-------------------
Voir la liste des database::
   $ mysql>show databases;  

Selectionner une database:: 
   $ mysql>use name_database

La liste des tables dans cette database::  
   $ mysql> show tables;

Requêtes
-------------------

SELECT : 

UPDATE : 

DELETE : 

Construction Base de données en Sql 
-------------------

Création::
   $ mysql> create database databasename;

Supprimer une base de données:: 
   $ mysql> drop database databasename;

Suppression d’une table::
    $ mysql> drop table tablename;

Création users
-------------------

Connexion:: 
   $ mysql -u root -p 
   $ mysql -h localhost -u root -p

localhost : nom de votre serveur mysql
u : user souhaité, ici root
p : signifie qu'il vas falloir entrer le pass de l'utilisateur

Créer users::
   $ mysql> CREATE USER 'users'@'localhost' IDENTIFIED BY 'mdp'; 

Donner les droits:: 
   $ mysql> GRANT ALL PRIVILEGES ON * . * TO 'users'@'localhost';

Pour que les droits prennent effet::
   $ mysql> FLUSH PRIVILEGES;

Listes des users::
   $ mysql> select * from mysql.user;


====== ============ =======
ID    Availability Name
====== ============ =======
1      N/A          Biros
2      42           piskoty
3      N/A          beton
====== ============ =======


