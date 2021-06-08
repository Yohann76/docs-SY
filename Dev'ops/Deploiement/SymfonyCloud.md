Synfony cloud
================

`Symfony Cloud official site`_

Instalation Synfony cloud
================
::

    curl -sS https://get.symfony.com/cli/installer | bash
    symfony login

Configuration
================
::

    symfony project:init
    git add .symfony.cloud.yaml .symfony/services.yaml .symfony/routes.yaml php.ini
    git commit -m "Add SymfonyCloud configuration"


Création du projet dans le cloud
================
::

    symfony project:create --title=demo --plan=development
    symfony deploy




.. _`Symfony Cloud official site`: https://symfony.com/cloud/