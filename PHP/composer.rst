ignorer les requirements d'un projet pour installer le vendor :
::

  composer install --ignore-platform-reqs
 
forcer une mise a jour d'un composant : 
::

  composer update akarah/hprim --no-cache --with-all-dependencies

installer une librairie github non publié :
::

  "repositories": [
        {
            "package": [
                {
                    "name": "akarah/hprim",
                    "version": "^1.0.0"
                }],
            "type": "vcs",
            "url": "https://github.com/Akarah/HPRIM"
        }
    ],
