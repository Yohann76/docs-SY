Mysql
===================

Show
-------------------
Voir la liste des database :
.. code-block:: terminal
    mysql>show databases;  

Selectionner une database: 
.. code-block:: terminal
    mysql>use name_database

La liste des tables dans cette database :  
.. code-block:: terminal   
    mysql> show tables;

Requêtes
-------------------

SELECT : 

UPDATE : 

DELETE : 

Construction Base de données en Sql 
-------------------

Création : 
.. code-block:: terminal
    mysql> create database databasename;

Console Output
--------------

Supprimer une base de données : 
.. code-block:: terminal
    mysql> drop database databasename;

Console Output
--------------

Suppression d’une table : 
.. code-block:: terminal
    mysql> drop table tablename;

Console Output
--------------


Création users
-------------------

Connexion : 
.. code-block:: terminal
    mysql -u root -p 
    mysql -h localhost -u root -p

Console Output
--------------

localhost : nom de votre serveur mysql
u : user souhaité, ici root
p : signifie qu'il vas falloir entrer le pass de l'utilisateur


Créer users : 
.. code-block:: terminal
    mysql>CREATE USER 'users'@'localhost' IDENTIFIED BY 'mdp'; 

Console Output
--------------

Donner les droits : 
.. code-block:: terminal
    mysql>GRANT ALL PRIVILEGES ON * . * TO 'users'@'localhost';

Console Output
--------------

Pour que les droits prennent effet : 
.. code-block:: terminal
    mysql>FLUSH PRIVILEGES;

Console Output
--------------

Listes des users: 
.. code-block:: terminal
    mysql>select * from mysql.user;

Console Output
--------------

