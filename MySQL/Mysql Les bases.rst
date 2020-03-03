.. index::
   single: Mysql; Show

Mysql
===================
`Mysql Doc <https://dev.mysql.com/doc/>`_

.. warning::
        Vous devez étre connecter pour effectuer les commandes


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

.. note::
        Exemple de table Mysql

====== ============ =======
ID    City          Name
====== ============ =======
1      NULL          Biros
2      NULL          piskoty
3      NULL          beton
====== ============ =======


