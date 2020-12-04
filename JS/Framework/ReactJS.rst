React.js ( Facebook ) 
===================

Commande pour monter un projet React 
####################

   composer require encore  / yarn add @symfony/webpack-encore --dev
   
- yarn 
- composer 

dépendances minimales 
#####################


::

   "@symfony/webpack-encore": "^0.19.0",
   "babel-preset-es2015": "^6.24.1",
   "babel-preset-react": "^6.24.1",
   "babel-preset-stage-0": "^6.24.1",
   "react": "^16.4.1",
   "react-dom": "^16.4.1",
   "react-on-rails": "^11.0.8",
   "react-transition-group": "^2.3.1"

- yarn add @babel/preset-react --dev
- yarn add react react-dom prop-types
- yarn install


Installer le point d'entrée dans twig:
#####################################

- {{ encore_entry_script_tags('main')}}


Dépendences yarn utiles : 
##########################

js eslint :
::

   yarn add eslint --dev ( détecte les violation de code js ) 

react eslint :
::

   yarn add eslint-plugin-react --dev ( détecte les violation de code react ) 


Installer react et react dom :
::

   yarn add react react-dom --dev


Comprendre le jsx :
::
   
   yarn add babel-preset-react --dev

Comprendre le jsx 2 :
::
   
   yarn add @babel/preset-react@^7.0.0 --dev

Vérification de data ( props ) :
::

   yarn add prop-types --dev


import PropTypes from 'prop-types';
::

   // Valid propTypes
   RepPhone.propTypes = {
      withHeart: PropTypes.bool,
      highlightedRowId: PropTypes.any,
      onRowClick: PropTypes.func.isRequired
   };

suppression de prototype en prod : yarn add babel-plugin-transform-react-remove-prop-types --dev

Génération de clé id pour ajax :
::

   yarn add uuid --dev   ( info ) 


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
::

   // Valid propTypes
   RepPhone.propTypes = {
      withHeart: PropTypes.bool,
      highlightedRowId: PropTypes.any,
      onRowClick: PropTypes.func.isRequired
   };


Héritage de props dans les composants( par sacha )
dans le composant parent : 
::

   <composantX
   propriété={‘hello’}
   />

dans le composant enfant :
accéder a la propriété avec : this.props.propriété

Possibilité de passer des états en props :
::

   <composantX
   etatX={this.state.StateX}
   />

Architecture entre Composant?
3 types de composants

Des composants intelligents ( logique métier ) qui impriment des composants stupide
Des composants stupide ( JSX ) 
Des composants réutilisable ( ex: un Composants button avec une props pour définir le texte sur le bouton ou sa couleur )

