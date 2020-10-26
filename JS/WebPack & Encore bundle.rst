Webpack
===================

Installation
Installer webpack avec yarn : yarn add webpack@3 --dev   ( ou webpack-cli )

Fonctionnement
-------------------
Exporter un objet, une variable, une classe, une fonction… :
exporter de module : module.exports = food
Importer un module : const foods = require(‘foods’);
const $ = require('jquery');
const Helper = require('./RepLogAppHelper')

après modification du webpack.config.js : exécuter “sh node_modules/.bin/webpack” pour builder le Js

Exemple de webpack.config.js :
::

   module.exports = {
      entry: {
         rep_log: './public/js/rep_log.js',
         login: './public/js/login.js',
      },
      output: {
         path: path.resolve(__dirname, 'public', 'build'),
         filename: '[name].js',
      }
   };


Webpack Encore
===================

Prendre sur nos git les bases
Webpackconfig.js [Copier]
package.json  [Copier]
App.scss  [Copier]
app.js  [Copier]
postcss.config  [Copier]
Installation :
$composer require symfony/webpack-encore-bundle
$yarn install ( pour exécuter le package.json )

Exécuter pour builder :
yarn watch ou yarn dev
yarn build pour la prod ( mimifie les fichier )

Ensuite chemin vers le fichier builder  dans base.html.twig
::

   {% block stylesheets %}
      {{ encore_entry_link_tags('app') }}
   {% endblock %}

   {% block javascripts %}
      {{ encore_entry_script_tags('app') }}
   {% endblock %}


Configuration webpack.config.js

Ajouter une entré :
::

   .addEntry('app', './assets/js/app.js')

Soit “app” le nom du fichier builder et ensuite le chemin du vrai fichier

Pour la gestion d’image avec webpack :
::

   // CopyFile
   .copyFiles({
      from : './assets/images',
      to: 'images/[path][name].[hash:8].[ext]'
   })

Pour supporter le SCSS :
::

   // enables Sass/SCSS support
   .enableSassLoader()


Exemple Syntaxe module
App.css :
::

   @import '~bootstrap';
   @import '~font-awesome';

   body {
      background-color: lightgray;
   }

App.js :
::

   import '../css/app.css';
   import getPhone from './get_phone';   // Fichier get_phone.js

Jquery environment
::

   import $ from 'jquery';
   import 'bootstrap'; // adds functionss to Jquery

Module get_phone.js exporter :
::
   export default function(exclamationCount) {
      return 'Hello Webpack EEncore! Edit me in assets/js/app.js'+'!'.repeat(exclamationCount);
   };


Production :
-------------------
::

  $Yarn install
  $Yarn build

Configuration webpack.config.js fonctionnel :
#############################################
::

  var Encore = require('@symfony/webpack-encore');
  Encore

      .setOutputPath('public/build/')
      // public path used by the web server to access the output path
      .setPublicPath('build')

      .addEntry('main', './assets/js/main.js')
      .configureBabel()
      .enableSingleRuntimeChunk()
      .cleanupOutputBeforeBuild()
      .copyFiles({
          from: './assets/images',
          to: 'images/[path][name].[hash:8].[ext]'
      })
      .splitEntryChunks()
      .autoProvidejQuery()
      //.enablePostCssLoader()
      .enableVersioning(Encore.isProduction())

      //react-Options
      .enableReactPreset()

  ;
  module.exports = Encore.getWebpackConfig();
