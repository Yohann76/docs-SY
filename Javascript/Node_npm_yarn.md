## Node.JS / yarn & npm

npm et yarn sont deux outils similaire pour gerer les dépendances javascript d'un projet front.

## Installer des dépendances globales :


Pour avoir accès a une librairie depuis n'importe ou, il faut installer les dépendances globalement avec -g ou -- global


## Checker les dépendance npm non utilisé :


    $ npm install -g npm-check
    $ npm-check


## Autre commandes NPM

    $ npm install -g npm // Mettre a jour npm
    $ npm init // Démarrer un projet npm ( avec les set config pré-rempli )
    $ npm rebuild // Recréer un projet npm ( peut résoudre des bugs )
    $ npm search <nompartiel> // Chercher un package avec son nom partiel
    $ npm dedupe // Résoudre les dépendences avec un rollback

## Utiliser pm2 :


pm2 est un utilitaire pour faire des cluster de serveur node et répartir la charge. pm2 permet de relancer un serveur en prod au démarrage du serveur, ou si celui-ci crash. pm2 permet de faire plusieurs instance node.

    $ npm install -g pm2 // installer pm2
    $ pm2 list // Lister les instances pm2
    $ pm2 start // Démarrer un projet pm2


Faire une image des processus et les redémarrer si la machine bug ou s'éteint :

    $ pm2 save


Configuration d'un fichier ecosystem.config.js


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

    $ pm2 start npm --name wikirunParse -- run npm start
