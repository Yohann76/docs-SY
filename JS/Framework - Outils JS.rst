Outils/Framework pour Javascript 
===================

Webpack 
-------------------
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
-------------------
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

// Jquery environment
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

$Yarn install
$Yarn build 

React.js ( Facebook ) 
Pré-requis yarn add : 

js eslint : yarn add eslint --dev ( détecte les violation de code js ) 
react eslint : yarn add eslint-plugin-react --dev ( détecte les violation de code react ) 
Installer react et react dom : yarn add react react-dom --dev
Comprendre le jsx : yarn add babel-preset-react --dev
Comprendre le jsx 2 : yarn add @babel/preset-react@^7.0.0 --dev
Vérification de data ( props ) : yarn add prop-types --dev
import PropTypes from 'prop-types';
// Valid propTypes
RepPhone.propTypes = {
   withHeart: PropTypes.bool,
   highlightedRowId: PropTypes.any,
   onRowClick: PropTypes.func.isRequired
};
suppression de prototype en prod : yarn add babel-plugin-transform-react-remove-prop-types --dev

Génération de clé id pour ajax : yarn add uuid --dev   ( info ) 


Autre prés-requis : 

Ajouter au webpack-config.js : .enableReactPreset() 
( pour bien compiler le JSX ) 

Avoir un fichier .eslintrc.js a la racine : 
::

	module.exports = {
   extends: ['eslint:recommended','plugin:react/recommended'],
   parserOptions: {
       ecmaVersion: 6,
       sourceType: 'module',
       ecmaFeatures: {
           jsx: true
       }
   },
   env: {
       browser: true,
       es6: true,
       node: true
   },
   rules: {
       "no-console": 0,
       "no-unused-vars": 0
   }
};

Vérification de Data ( props ) 
Vérification de data ( props ) : yarn add prop-types --dev
import PropTypes from 'prop-types';
// Valid propTypes
RepPhone.propTypes = {
   withHeart: PropTypes.bool,
   highlightedRowId: PropTypes.any,
   onRowClick: PropTypes.func.isRequired
};
Héritage de props dans les composants( par sacha )
dans le composant parent : 
<composantX
  propriété={‘hello’}
/>
dans le composant enfant :
accéder a la propriété avec : this.props.propriété

Possibilité de passer des états en props :
<composantX
 etatX={this.state.StateX}
/>

Architecture entre Composant?
3 types de composants

Des composants intelligents ( logique métier ) qui impriment des composants stupide
Des composants stupide ( JSX ) 
Des composants réutilisable ( ex: un Composants button avec une props pour définir le texte sur le bouton ou sa couleur )



Angular.js ( google ) 
-------------------
Installation 
node requis.

npm install -g npm@latest
installer Angular/cli 
npm install -g @angular/cli

créer un projet : 
ng new mon-premier-projet
cd mon-premier-projet
ng serve --open ( demarrer le serveur )

Destination : localhost:4200




Fonctionnement 
