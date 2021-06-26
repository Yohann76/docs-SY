
Node.JS / yarn & npm
===================


npm et yarn sont deux outils similaire pour gerer les dépendances javascript d'un projet front.

Installer des dépendances globales :
----------------------------------------

Pour avoir accès a une librairie depuis n'importe ou, il faut installer les dépendances globalement avec -g ou -- global


Checker les dépendance npm non utilisé :
-------------------

::

  npm install -g npm-check

::

  npm-check

Mettre a jour npm
--------------------

::

  npm install -g npm

Démarrer un projet npm ( avec les set config pré-rempli )
-----------------------

::

  npm init

Recréer un projet npm ( peut résoudre des bugs )
-------------

::

  npm rebuild


Chercher un package avec son nom partiel
----------------------------

::

  npm search <nompartiel>


Résoudre les dépendences avec un rollback :
--------------------------

::

  npm dedupe

Utiliser pm2 :
--------------------------
pm2 est un utilitaire pour faire des cluster de serveur node et répartir la charge. pm2 permet de relancer un serveur en prod au démarrage du serveur, ou si celui-ci crash. pm2 permet de faire plusieurs instance node.

installer pm2
::

  npm install -g pm2


Lister les instances pm2
::

  pm2 list

Démarrer un projet pm2
::

  pm2 start


Faire une image des processus et les redémarrer si la machine bug ou s'éteint :
::

  pm2 save


Configuration d'un fichier ecosystem.config.js
::
  module.exports = {
    apps : [{
      name: "wikirun-parse-server",
      script: "yarn",
      args: "start",
      cwd:"/var/www/wikirun-parse-server/index.js",
      autorestart: true,
      env: {
        NODE_ENV: 'development'
      },
      env_production: {
        NODE_ENV: 'production',
        //API_URL: 'YOUR ENV URL',
        PORT:1337
      }
    }]
  };




[package npm](https://www.npmjs.com/package/npm-check)



Lancer une instance plus complexe en cas de bug :
::

  pm2 start npm --name wikirunParse -- run npm start