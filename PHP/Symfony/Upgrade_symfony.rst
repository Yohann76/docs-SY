##################
Upgrade Symfony Version
##################

`Cours SymfonyCast migration 3.0 a 4.0/4.4  <https://symfonycasts.com/screencast/symfony4-upgrade/framework-config>`_
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

- ( mettre 4.4 sur le composer.json ) -> composer update & composer install
- mettre a jour le composer.json ( enlever le symfony/symfony) & prendre exemple sur Symfony/demo ( enlever la replace section )
- composer update & composer install
- composer require annotations asset orm-pack twig logger mailer form security translation validator
- composer require --dev dotenv maker-bundle orm-fixtures profiler
- Ajouter notre propre configuration de service a partir de service.yml
- Deplacer app/Resources/views => templates
- Deplacer app/Resources/translations/ => translations ( dossier)
- app/Resources/<BundleName>/views/ => templates/bundles/<BundleName>/
- reste des app/Resources/ => src/resources/

------

- deplacer src/Appbundle/* ( sauf AppBundle.phpet DependencyInjection/ ) vers /src/
- mettre a jour les valeur d'autoload et autoload-dev dans le composer.json
- Déplacer les biens publics, tels que des images ou des fichiers compilés CSS / JS, à partir src/AppBundle/Resources/public/de public/(par exemple public/images/).
- Déplacez la source des actifs (par exemple les fichiers SCSS ) vers assets/et utilisez Webpack Encore pour les gérer et les compiler.
- SYMFONY_DEBUGet SYMFONY_ENVles variables d'environnement ont été remplacées par APP_DEBUGet APP_ENV. Copiez leurs valeurs dans les nouveaux vars, puis supprimez les anciens.
- Créez le nouveau public/index.phpcontrôleur frontal en copiant la source index.php de Symfony et, si vous avez effectué une personnalisation dans vos fichiers web/app.phpet web/app_dev.php, copiez ces modifications dans le nouveau fichier. Vous pouvez maintenant supprimer l'ancien web/répertoire.
- retirer src/Appbundle
- Déplacez le code source d'origine de et mettez src/{App,...}Bundle/à src/jour les espaces de noms de chaque fichier PHP App\...(les IDE avancés peuvent le faire automatiquement).
- Supprimez le bin/symfony_requirementsscript et si vous avez besoin d'un remplacement pour lui, utilisez le nouveau Symfony Requirements Checker .
- Mettez à jour le .gitignorefichier pour remplacer l' var/logs/entrée existante par var/log/, qui est le nouveau nom du répertoire des journaux.

A partir de Symfony 4.4 -> Symfony 5.4
=======================================




##################
DEPRECIATION
##################






