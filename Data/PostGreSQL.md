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

    $ CREATE DATABASE bdd_drag_drop; // créer une bdd
    $ DROP DATABASE bdd_drag_drop; // supprimer une bdd
    $ \l // lister les bases de données
    $ \d nametable // Lister les champs d'une table
    $ \c bdd_drag_drop // se connecter a la base
    $ \d // Lister les tables
    $ CREATE TABLE books(title varchar(128), author varchar(128), price int, date date); // créer une table
    $ DROP TABLE alembic_version CASCADE; // supprimer une table en cascade
    $ psql -h 127.0.0.1 -U postgres // connexion depuis le WSL2 Windows

Se déconnecter d'une bdd:


  relancer le shell

Les select :

    $ SELECT * FROM books;
    $ SELECT * FROM books WHERE price < 28;

Connexion a la bdd en ligne de commande :


    $ psql -U tqa_owner tqa_dataservice

Utiliser la base :


    \c tqa_dataservice

recherche :


    SELECT * FROM patients WHERE last_name = 'Zola';
