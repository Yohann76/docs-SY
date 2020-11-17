PostGreSQL
===================

PostGreSQL s'installe ici
`PostGreSQL download`_

1. Suivre l'installation
2. Redemarrer le PC
3. Chercher l'application SQL Shell (psql) dans le menu démarrer ( pas de raccourci installé après l'installation )

Sur le shell, les commandes psql sont disponibles
( taper plusieurs fois entrée pour les parametre par defaut, et taper le mot de passe ):

  create database bddDragDrop;
  create database bddDragDrop;

lister les bdd:
::

  \l

se connecter a la base :
::

  \c bddDragDrop

créer une table :

  create table books(title varchar(128), author varchar(128), price int, date date);

Lister les tables :
::

  \d

supprimer une table 
::

  drop table alembic_version
    
    
selection:

- select * from books;
- select * from books where price < 28;

.. _`PostGreSQL download`: https://www.postgresql.org/download/windows/
