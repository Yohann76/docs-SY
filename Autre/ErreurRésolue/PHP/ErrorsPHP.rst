PHP
===================

Erreur Mémoire dans php
-------------------
Erreur a l'execution d'un "composer update" 
Erreur : "PHP Fatal error: Allowed memory size of XXXXXX bytes exhausted <...>"
::

    ; Maximum amount of memory a script may consume (128MB)
    ; http://php.net/memory-limit
    memory_limit = 400M

Variable de base a "128M"
Maximum de la variable "5000M" ? 

Variable à modifier dans le php.ini

ou bien :
::

    php -dmemory_limit=-1 c:\composer\composer.phar update

autre erreur : 
-------------------