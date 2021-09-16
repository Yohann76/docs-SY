## PostGreSQL


PostGreSQL s'installe ici
[PostGreSQL download](https://www.postgresql.org/download/windows/)


1. Suivre l'installation
2. Redemarrer le PC
3. Chercher l'application SQL Shell (psql) dans le menu démarrer ( pas de raccourci installé après l'installation )

Sur le shell, les commandes psql sont disponibles
( taper plusieurs fois entrée pour les parametre par defaut, et taper le mot de passe ):


Ligne de connexion à la BDD


    // DATABASE_URL=postgres://dauser:dapassword@localhost:5432/dadb
    Server : localhost ( default )
    Database : PostGreSQL ( default )
    Port : 5432 ( default )
    Username : dauser
    password : dapassword

## Divers commandes

    $ create database bddDragDrop; // créer une bdd
    $ drop database bddDragDrop; // supprimer une bdd
    $ \l // lister les bases de données
    $ \d nametable // Lister les champs d'une table
    $ \c bddDragDrop // se connecter a la base
    $ \d // Lister les tables
    $ create table books(title varchar(128), author varchar(128), price int, date date); // créer une table
    $ DROP TABLE  alembic_version CASCADE; // supprimer une table

Se déconnecter d'une bdd:


  relancer le shell

Les select :

    $ select * from books;
    $ select * from books where price < 28;

Connexion a la bdd en ligne de commande :


    $ psql -U tqa_owner tqa_dataservice

Utiliser la base :


    \c tqa_dataservice

recherche :


    mysql> SELECT * from patients WHERE last_name = 'Zola';
