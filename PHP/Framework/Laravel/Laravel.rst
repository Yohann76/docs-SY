Laravel 
===================

Démarrage Laravel : 
--------------------

Command:
::

  composer create-project laravel/laravel laravel5 --prefer-dist
  
Créer un .env:
::
  
  APP_ENV=local
  APP_DEBUG=true

  APP_KEY=base64:JjrFWC+TGnySY2LsldPXAxuHpyjh8UuoPMt6yy2gJ8U=
  

Architecture
------------

- config
- database
- docker
- public
- ressource
- routes
- storages
- tests
- app
- bootstrap
- vendor


Command 
---------
Lancer le serveur laravel intégré : 
::

  php artisan serve --host 0.0.0.0 --port 8082
  
  
Générer une key :
::

  php artisan key:generate
  
Clear la config et MAJ :
::
  
  php artisan config:cache
  
  
Effectuer une migration:
::

  php artisan migrate
