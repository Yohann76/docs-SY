Composer
===================

`Composer docs`_

Commande Composer :
===================
::

    Composer install // installer les dépendance dans le composer.json
    Composer update // update les dépendance
    composer remove // delete
    composer outdated // Permet de lister les paquets obsolètes et qui auraient besoin d’une mise à jour (si possible, à adapter selon votre cas).
    composer show // lister les paquets installés sur votre projet



Options Composer
===================
::

    --verbose (-v): Increase verbosity of messages.
    --help (-h): Display help information.
    --quiet (-q): Do not output any message.
    --no-interaction (-n): Do not ask any interactive question.
    --no-plugins: Disables plugins.
    --no-cache: Disables the use of the cache directory. Same as setting the COMPOSER_CACHE_DIR env var to /dev/null (or NUL on Windows).
    --working-dir (-d): If specified, use the given directory as working directory.
    --profile: Display timing and memory usage information
    --ansi: Force ANSI output.
    --no-ansi: Disable ANSI output.
    --version (-V): Display this application version.

    --name: Name of the package.
    --description: Description of the package.
    --author: Author name of the package.
    --type: Type of package.
    --homepage: Homepage of the package.
    --require: Package to require with a version constraint. Should be in format foo/bar:1.0.0.
    --require-dev: Development requirements, see --require.
    --stability (-s): Value for the minimum-stability field.
    --license (-l): License of package.



    .. _`Composer docs`: https://getcomposer.org/doc/
