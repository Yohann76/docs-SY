Laravel 
===================

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
