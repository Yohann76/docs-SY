## Problem Windows-MacOS compabilité


Probléme de ré-écriture windows ( clone d'un projet MAC et executer un docker sur windows )


    $ git config --global core.autocrlf false
    $ git config --global core.autocrlf true // pour restaurer le comportement git de base seulement

Lien du probléme : [Docker_exec_with_clone_for_docker](https://stackoverflow.com/questions/29045140/env-bash-r-no-such-file-or-directory/29045187#29045187)

Modifier une variable d'environement en ligne de commande

    $ export FLASK_ENV=development // export = mac
    $ set FLASK_ENV=development // set = windows

## Execution d'un fichier

    $ pipenv run ./wsgi.py // ./ = mac
    $ pipenv run wsgi.py // juste le nom de fichier = windows
