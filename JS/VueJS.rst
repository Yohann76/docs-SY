Vue JS
===================

`Vue Docs`_

Vue.js est un framework qui permet de ne pas charger les pages dans leurs intégralité, mais seulement par morceaux, pour des raisons de quantité de donnée et de fluidité. Vue.js est une technologie populaire dans le frontend. Il est connu pour sa facilité de prise en main, même a l'arrivée de projets complexe, et les développeurs deviennet plus productif. Vue est accueillant et sa documentation est remarquable. Un bon choix comme premier framework front.


Installation de vue 
=====================

Via un simple lien CDN : 
::
    <!DOCTYPE html>
      <html lang="en">
      <head>
          <title>Mon Application Vue.js</title>
      </head>
      <body>
          <div id="app">
              <h1>Ma première application Vue.js !</h1>
              <p>J'ai hâte de créer des applications incroyables !</p>
          </div>
          <script src="<https://cdn.jsdelivr.net/npm/vue>"></script>
      </body>
      </html>
  
Tester le fonctionnement de vue : 
::
  <!DOCTYPE html>
    <html lang="en">
    <head>
        <title>Mon Application Vue.js</title>
    </head>
    <body>
        <div id="app">
            <h1>Ma première application Vue.js !</h1>

            <p>J'ai hâte de créer des applications incroyables !</p>
        </div>
        <script>
        // Vue n'est pas encore chargé donc une RefenreceError devrait être retournée
        console.log(Vue)
        </script>
        <script src="<https://cdn.jsdelivr.net/npm/vue>"></script>
        <script>
            // La console devrait maintenant afficher une fonction
            console.log(Vue)
        </script>
    </body>
    </html>

Pour commencer une application :Ajoutez Vue.js à  index.html  pour le convertir en application monopage.
Definir ou vue devrait apparaitre sur une page ( pour decider de ce vue peut controller, Vue est spécialisé dans les application SPA : monopage  )
::
  <script>
    const app = new Vue({
      el: '#app'
    })
  </script>
  
Base de Vue.js
=====================

Nous pouvons stocker des donner avec l'attribut data, qui peut prendre en charge des variables. 
::
    const app = new Vue({
        el: '#app',
        data:{
            variable: 1,
            string: 'hello'
        }
    })
    
Les données peuvent être afficher avec la syntaxe "en moustache" dans du HTML
::
    {{ variable }}
    {{ (2 + 8) *10 }}
    {{ variable.toUpperCase() }}
    {{ 2 > 0 ? 'Deux est plus grand que zéro' : 'Vous ne verrez jamais cette phrase' }}

.. _`Vue Docs`: https://fr.vuejs.org/v2/guide/
