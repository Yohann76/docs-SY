## JavaScript

## Base du javascript

## Les tableau

    var fruits = ['Apple', 'Banana'];
    console.log(fruits.length); // compter le nombre d'éléments
    var first = fruits[0]; // acceder à un élément
    var newLength = fruits.push('Orange'); // ajouter a la fin d'un tableau
    var newLength = fruits.unshift('Strawberry') // ajoute au début
    var pos = fruits.indexOf('Banana'); // Trouver l'index d'un tableau // 1
    var last = fruits.pop(); // Supprimer le dernier élément du tableau
    passer les éléments d'un tableau sur une boucle :
    let sequence = [1, 1, 2, 3, 5, 8, 13];
    for (var i = 0; i < sequence.length; i++) {
      console.log(sequence[i]);
    }
    fruits.splice(indexPosition, 1); // supprimer un élément du tableau a un index précis

## Les variables

## Divers elements utile en JS

    window.location.reload(true); // recharger la méme url // true = on serve, false = on cache


    var x = 1; // Déclarer une variable
    let varTxt = 'La révolution ne sera pas télévisée.'; // Déclarer une vairable chaine de caractére

Définition d’un objet :


  	var objet = {
          var xxxxx = ‘xxxx’;
          var2 xxxxx = 51 ;

          function initialize(){}
          function xxxx(){}
      }

## Sélection des éléments

    document.getElementById(‘monId’);
    document.getElementsByName(‘monId’);
    document.getElementsByClassName(‘class’);


Méthode sur sur les éléments ( représenté par variable )


    variable.style[‘color’] = ‘green’; // modifier le css d’un élément
    variable.length; // compter le nombre de caractère
    variable.add(‘new class’); // ajouter une class a l’élément :
    variable.append(‘new class’);  //( || appendChild ) // ajouter a l'élément

Événement sur sur les éléments ( représenté par variable )

    variable.click; // ( appui sur l'élément )
    variable.double click; //(double-click)
    variable.input; //( surveiller l’entrée dans un champ texte )
    variable.select; //( sélectionner le contenu d’un textArea )
    variable.mouseover; // ( survol )


lire un attribut data-url :

    $(this).data('url');

Rechercher chaque élément :

    $element.find(‘tbody tr’).each(function(){       });

utilisable directement dans le html :


  span id=”input” onclick=”alert(‘vous avez cliqué’)”></span>


## Fonctions Sympathique

    console.log(xxx);   // affiche quelque chose sur la console ( texte,variable,objet..)
    console.dir(objet);  // affiche les méthode et attribut d’un objet
    alert();
    JSON.stringify() ; //  convertit une valeur JavaScript en chaîne JSON.

## Appel AJAX et fonctions asynchrone

Appel AJAX Simple :

    $.ajax(
          {
          url: deleteUrl,
          method: ‘DELETE’,
          success:
          function(){
              $row.fadeOut();
          }

      // other exemple
      $('#mySubmitButton').attr("disabled",true);
        $.ajax({
        url: "{{ path('new_mission_json') }}",
        type: 'POST',
        dataType: 'json',
        data: form_data,
        processData: false, // for ilegal invoc error
        contentType: false,

        success:function(data){
          if(data.status == 'error'){
            console.log("[API] ERROR: "+data.message);
                // To do : display error in html
          }
          if(data.status == 'success'){
            console.log("[API] SUCCESS: "+ data.message);

                $('#myModal-1').modal('hide'); // close modal

                // reload page with cookie ?
                // for reload on /edit or /new
                window.location.reload(true); // reload page, true = reload on serve, false = on cache
      }

API & Annexe a Javascript
POO Javascript
Objet  $this : Fait référence à l’objet dans lequel nous sommes actuellement
objet window : variable globale

Démonstration d’un objet :


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

## Syntaxe :



  	var clickme = document.getElementById('clickme');
      clickme.addEventListener('click', function(e) {
          e.target.innerHTML = 'Vous avez cliqué !';
      });

## ES6 ou ES 2015:

déclaration de fonction : =>
déclaration de variable : possible avec let a la place de var ( Let a la portée d’un bloc, moins d’erreur si la variable est pas défini )
classe d’objet uniquement avec ES6
boucle for of : for (let element of $elements) {}
type d’objet : Map ; WeakMap


## Yarn

Yarn est un gestionnaire de dépendance JS :
installer yarn avec un exécutable msi

obtenir yarn (package.json) sur un projet : yarn init

Installation :


    babel : yarn add babel-cli --dev
    jquery : yarn add jquery
    sweet-alert : yarn add sweetalert2@6.6.6 --dev
    Bootstrap : yarn add bootstrap@3 --dev
    Bootstrap-sass : yarn add bootstrap-sass --dev

Liste complètes des dépendances pour réact sur son propre fichier.

Les dépendances installer se trouve dans node module et sont installable directement en téléchargeant le package.json avec yarn install
