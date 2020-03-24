##################
Upgrade Symfony Version
##################

::
    // Program
    3.1 -> 3.3 -> symfony flex -> 3.4 -> 4.4


A partir de Symfony 3.1 -> Symfony 3.3
=======================================

::
    //composer.json
    "symfony/symfony": "3.3.*",

::
    > composer update
    > composer install


A partir de Symfony 3.3 -> Symfony 3.4
=======================================

:: 
    > composer self-update
    > composer require symfony/flex

::
    > rm -Rf vendor
    > composer install
    

TODO: Changer composer.json 


::
    //composer.json
    "symfony/symfony": "3.4.*",

::
    > composer update
    > composer install


A partir de Symfony 3.4 -> Symfony 4.4
=======================================

1. Mettre a jour le composer. json 
- enlever symfony/symfony et faire un composer update pour installer les recettes flex
- enlever les bundles et paquets inutiles pour les remplacer par les nouveaux supporté
- enlever les probleme de conflit

2. Faire le systeme de double application ( autoload double chargement )

::
    "autoload": {
        "psr-4": {
            "": "src/"
        },
        "classmap": [
            "app/AppKernel.php",
            "app/AppCache.php"
        ]
    },
    "autoload-dev": {
        "psr-4": {
            "Tests\\": "tests/"
        }
    },

3. mettre a jour le bin/console via https://github.com/symfony/recipes/blob/master/symfony/console/3.3/bin/console


4. migrer la sécurité 
- migrer les configuration de chaque service ( /app/config/* )vers les fichiers nouveaux fichiers config (/config/*)
- s'il n'y a pas de fichiers prévu pour migrer la config : Intaller les composants manquant pour que les recettes ajoute la config nécéssaire.
- security.yaml peut etre entierement copier-coller
- migrer les config_[env].php, vers config/package/[env]/[config]

5. migrer les template de /app/Resource/view vers templates/

6. migrer src/AppBundle vers src/
7. migrer web/* vers public/
8. Retirer appbundle et remplacer les occurences de AppBundle par App
9. Enlever l'autoload de double chargement



A partir de Symfony 4.4 -> Symfony 5.4
=======================================





##################
DEPRECIATION
##################






