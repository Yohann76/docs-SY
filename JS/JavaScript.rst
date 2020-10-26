.. index::
   single: JavaScript;

JavaScript
===================

Base du javascript
-------------------
Normalisation:
préfixer js-xxxxx a toute les class de div qui servent pour le javascript

Base :
Définition de variable :
::
    var variable = 3;

Définition d’un objet :
::

	var objet = {
        var xxxxx = ‘xxxx’;
        var2 xxxxx = 51 ;

        function initialize(){}
        function xxxx(){}
    }

Sélection des éléments
-------------------
::

	document.getElementById(‘monId’);
    document.getElementsByName(‘monId’);
    document.getElementsByClassName(‘class’);


Méthode sur sur les éléments ( représenté par variable )
modifier le css d’un élément :
::
    variable.style[‘color’] = ‘green’;

compter le nombre de caractère :
::
    variable.length;

ajouter une class a l’élément :
::
    variable.add(‘new class’);

ajouter a l'élément :
::
    variable.append(‘new class’);  //( || appendChild )

lire un attribut data-url :
::
    $(this).data('url');

Rechercher chaque élément :
::
    $element.find(‘tbody tr’).each(function(){       });


Événement sur sur les éléments ( représenté par variable )
::

    variable.click; // ( appui sur l'élément )
    variable.double click; //(double-click)
    variable.input; //( surveiller l’entrée dans un champ texte )
    variable.select; //( sélectionner le contenu d’un textArea )
    variable.mouseover; // ( survol )

utilisable directement dans le html -> span id=”input” onclick=”alert(‘vous avez cliqué’)”></span>


Fonctions Sympathique
-------------------
::

    console.log(xxx);   // affiche quelque chose sur la console ( texte,variable,objet..)
    console.dir(objet);  // affiche les méthode et attribut d’un objet
    alert();

Appel AJAX et fonctions asynchrone
-------------------

Appel AJAX Simple :
::

	$.ajax(
        {
        url: deleteUrl,
        method: ‘DELETE’,
        success:
        function(){
            $row.fadeOut();
        }

API & Annexe a Javascript
POO Javascript
Objet  $this : Fait référence à l’objet dans lequel nous sommes actuellement
objet window : variable globale

Démonstration d’un objet :

::

	class RepLogApp {
       constructor($wrapper) {
           this.$wrapper = $wrapper;
           this.helper = new Helper(this.$wrapper);
           this.loadRepLogs();
           this.$wrapper.on(
               'click',
               '.js-delete-rep-log',
               this.handleRepLogDelete.bind(this)
           );

           this.$wrapper.on(
               'click',
               'tbody tr',
               this.handleRowClick.bind(this)
           );

           this.$wrapper.on(
               'submit',
               this._selectors.newRepForm,
               this.handleNewFormSubmit.bind(this)
           );
       }
    }

Syntaxe :
-------------------
::

	var clickme = document.getElementById('clickme');
    clickme.addEventListener('click', function(e) {
        e.target.innerHTML = 'Vous avez cliqué !';
    });

ES6 ou ES 2015:
-------------------

déclaration de fonction : =>
déclaration de variable : possible avec let a la place de var ( Let a la portée d’un bloc, moins d’erreur si la variable est pas défini )
classe d’objet uniquement avec ES6
boucle for of : for (let element of $elements) {}
type d’objet : Map ; WeakMap


Yarn
-------------------
Yarn est un gestionnaire de dépendance JS :
installer yarn avec un exécutable msi

obtenir yarn (package.json) sur un projet : yarn init

Installation :
::

    babel : yarn add babel-cli --dev
    jquery : yarn add jquery
    sweet-alert : yarn add sweetalert2@6.6.6 --dev
    Bootstrap : yarn add bootstrap@3 --dev
    Bootstrap-sass : yarn add bootstrap-sass --dev

Liste complètes des dépendances pour réact sur son propre fichier.

Les dépendances installer se trouve dans node module et sont installable directement en téléchargeant le package.json avec yarn install
Node.js:
Executer un fichier js avec node : node nom_du_fichier


Jquery
-------------------
Sélection du DOM
::

	$(document).ready(function() {
    $('.class').on('click', function() {
            console.log('todo delete!');
        });
    }
