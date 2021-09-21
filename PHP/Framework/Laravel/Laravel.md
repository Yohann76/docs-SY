## Laravel

## Démarrage Laravel :

## Créer Laravel avec Composer

    $ composer create-project laravel/laravel laravel5 --prefer-dist

Créer un .env:

    APP_ENV=local
    APP_DEBUG=true
    APP_KEY=base64:JjrFWC+TGnySY2LsldPXAxuHpyjh8UuoPMt6yy2gJ8U=

## Architecture

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

## Commande principal


    $ php artisan serve --host 0.0.0.0 --port 8082 // Lancer le serveur laravel intégré
    $ php artisan key:generate // Générer une key
    $ php artisan config:cache // Clear la config et MAJ
    $ php artisan migrate // Effectuer une migration
    $ php artisan test --coverage-html tests/coverage // Lancer les tests avec coverage
