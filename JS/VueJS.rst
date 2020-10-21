Vue JS
===================

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
    
Definir ou vue devrait apparaitre sur une page ( pour decider de ce vue peut controller, Vue est spécialisé dans les application SPA : monopage  )
::
  <script>
    const app = new Vue({
      el: '#app'
    })
  </script>
  
  

`Vue Docs`_

.. _`Vue Docs`: https://fr.vuejs.org/v2/guide/
