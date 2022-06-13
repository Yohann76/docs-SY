## Mysql


[Mysql Doc](https://dev.mysql.com/doc/)

## Commandes courante


Voir la liste des database

    $ mysql> show databases; // list des database
    $ mysql> use name_database // Selectionner une database
    $ mysql> show tables; // La liste des tables dans cette database
    $ mysql> SELECT * FROM user; // voir le contenu de toute la table user


## Gestion User

    UPDATE mysql.user SET password=PASSWORD("wikipass") where User="zabbix"; // change password
    UPDATE mysql.user SET passwd="wikipass" where User="zabbix"; // change password
    ALTER USER 'zabbix'@'ip_address' IDENTIFIED WITH mysql_native_password BY 'wikipass'; // changer le type de mot de passe
    FLUSH PRIVILEGES; // Sauvegarder les modifications en ligne de commande

## Commande divers

    $ mysql> describe tablename; // Afficher la les types des champs
    $ mysql> ALTER TABLE `risk` CHANGE `description` `description` LONGTEXT // Modifier le type de text de la colonne description dans la table risk
    $ mysql> SELECT table_schema "Databases", sum( data_length + index_length) / 1024 / 1024 "Size of DB in MB" FROM information_schema.TABLES GROUP BY table_schema; // Afficher la taille des base de données


## Lister les clefs etrangère sur une database

    SELECT * FROM INFORMATION_SCHEMA.TABLE_CONSTRAINTS WHERE `table_schema` LIKE 'database_name' AND `constraint_type` = 'FOREIGN KEY';

## Requêtes et gestion des données


### SELECT :

    $ SELECT * FROM membres ;
    $ SELECT pseudo FROM membres WHERE id_membre BETWEEN 40 AND 60

### UPDATE :

    $ UPDATE `membres` SET `email`="p@pierre.fr" WHERE `id`=1; // Modifier tout ID
    $ UPDATE `membres` SET `email`="jacques@monfai.fr", `pseudo`="Jacques" WHERE `id`=1;  // supprimer seulement ID 1

### DELETE :

    $ DELETE FROM `membres`; // supprimer TOUT les membres
    $ DELETE FROM `membres` WHERE `id`=1; // supprimer le membre avec id 1

Les commandes précedentes peuvent être suivi d'une clause WHERE pour préciser une condition.


## Commande relative à la gestion de la bdd


    $ mysql> create database databasename; // Création bdd
    $ mysql> drop database databasename; // Supprimer une base de données
    $ mysql> drop table tablename; // Suppression d’une table


## Création user

Créer un user SQL et transférer ses droits :

    CREATE USER 'user1'@'localhost' IDENTIFIED BY '000000'; // créer
    GRANT ALL PRIVILEGES ON * . * TO 'user1'@'localhost'; // donner les droit
    FLUSH PRIVILEGES; // pour faire prendre effet les droits

## Connexion

    $ mysql -u root -p
    $ mysql -h localhost -u root -p // connexion en tant que root password = root

( détails de la commande de connexion )

localhost : nom de votre serveur mysql
u : user souhaité, ici root
p : signifie qu'il vas falloir entrer le pass de l'utilisateur


Listes des users

    $ mysql> select * from mysql.user;


## Sauvegarde et restauration


    $ mysqldump -u username -p --databases databasename > databasename.sql // Sauvegarder une seule base de donnée, données et structure
    $ mysqldump -uroot -p --all-databases > alldatabases.sql // Sauvegarder toutes les bases, données et structure, dans un seul fichier .sql
    $ mysql -u username -p databasename < databasename.sql // Restaurer une base à partir d'un fichier .sql contenant une sauvegarde de la base
    $ mysql -u username -p --one-database mybase < alldatabases.sql // Restaurer une base à partir d'un fichier. sql contenant une sauvegarde de toutes les bases

    $ mysqldump --user=mon_user --password=mon_password --databases nom_de_la_base_1 nom_de_la_base_2 > fichier_destination.sql // Pour sauvegarder plusieurs bases de données
    $ mysqldump --user=mon_user --password=mon_password --databases nom_de_la_base > fichier_destination.sql // Pour sauvegarder une base de données précise
    $ mysql --user=mon_user --password=mon_password nom_de_la_base < fichier_source.sql // restaurer dans une base de données précise

    $ mysqldump -u root -pxxxxxx test2 > test2backup.sql // sauvegarde
    $ mysql -u root -pxxxxxx test < test2backup.sql // restauration

## Dump avec condition

    $ mysqldump -umy_user_name -p database_name  --tables my_table1 --where="date_created > '2016-01-01' " > mytable1_filtered_dump.sql
    $ mysqldump -t -u root -p  mytestdb mytable --where="datetime LIKE '2014-09%'"
    $ mysqldump my_db_name my_table_name --where="id > 500" > my_backup.sql


## Requete d'Insertion


    $ mysql> INSERT INTO user_orga VALUES (33, 50, 17, 'ROLE_ORGA_DPO', NULL);  // dans la table user orga aprés avoir choisis d'utiliser la bdd correspondante


## Configuration & info :


  SHOW VARIABLES WHERE Variable_name = 'port'; // requete SQL pour savoir le port de mysql

## Utilisation MySQL WorkBench

Connexion à une bdd sur un serveur distant :

Standart TCP/IP with SSH :

  SSH HostName : Ip server
  SSH username : ubuntu
  SSH password : ssh password

  MySQL Hostname : localhost
  MySQL Server Port : 3306
  Username : username mysql
  mysql pass : password mysql


Sur l'onglet "Query" des scripts peuvent etre effectué :

    show databases;
    use blitz;
    select * from user;

    Controle + enter pour executer le script


à droite du resultat, nous pouvons modifier un element avec un formulaire.
