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


A partir de Symfony 4.4 -> Symfony 5.4
=======================================




##################
DEPRECIATION
##################






