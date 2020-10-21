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
          <script src="https://cdn.jsdelivr.net/npm/vue@2.6.12/dist/vue.js"></script>
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
        <script src="https://cdn.jsdelivr.net/npm/vue@2.6.12/dist/vue.js"></script>
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

Nous pouvons écrire des fonctions pré-compilé, comme pour le total de panier d'achat:
::
    <html>
    <body>
      <div id="app">
        <h2>Panier</h2>
          <li>Pommes: {{ costOfApples }}€</li>
          <li>Bananes: {{ costOfBananas }}€</li>
          <li>Noix de coco: {{ costOfCoconuts }}€</li>
        <p>Total: {{ totalAmount }}€</li>
      </div>

      <script>
        const app = new Vue({
          el: '#app',
          data: {
            costOfApples: 6,
            costOfBananas: 2,
            costOfCoconuts: 8
          },
          computed: {
            totalAmount() {
              return this.costOfApples + this.costOfBananas + this.costOfCoconuts //  ( afficher avec {{ totalAmount }}
            }
          }
        })
      </script>
    </body>
    </html>

Directives
=====================

Les directive permettent de résoudre les probleme courant. Elle sont écrit de manière semantique, elles ressemble a des attributs HTML, elle se préfixe par v-
( v-show ; v-if ; v-for ; v-model ; v-on ; v-bind ; v-else-if ; v-else )
::
    <div id="app">
        <!-- Si (if) l'utilisateur a les autorisations par défaut, afficher ce qui suit -->
        <section v-if="userPermission === 'default'">...</section>
        <!-- Sinon et si l'utilisateur a les autorisations administrateur, afficher ce qui suit -->
        <section v-else-if="userPermission === 'admin'">...</section>
        <!-- Si l'utilisateur n'a aucune autorisation afficher ce qui suit -->
        <section v-else>...</section>
    </div>

v-show est utilisté pour les éléments de toggle, pour controler la visibilité d'un élément avec une permutation fréquente comme une modale
::
    <div id="app">
        <button>Display Modal</button>
        <div v-show="showModal" class="modal">...</div>
    </div>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                showModal: false
            }
        })
    </script>

une boucle for
::
    <div id="app">
        <h1>Vue Mart</h1>
        <h2>Shopping Cart</h2>
        <ul>
            <li v-for="item in shoppingCart">
                {{ item.label }} : {{ item.cost }}€
            </li>
        </ul>
    </div>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                shoppingCart: [
                    { label: 'Pommes', cost: 6 },
                    { label: 'Bananes', cost: 2 },
                    { label: 'Noix de coco', cost: 8 {
                ]
            }
        })
    </script>

v-bind est utile pour les lien, elle peut être raccourci par un ':', v-bind est utilisé pour renvoyer des donnée issue d'API, ou des données en fonction d'autre systême.
::
    v-bind:href="item.url"

Les évenements
=====================

Voici commencer créer un evenement avec la directive v-on
::
    <div id="app">
        <button v-on:click="alert('Bonjour')">Cliquez ici !</button>
    </div>

peut être abrégé en : @click="alert('Bonjour')"

Un évenement peut faire appel au méthodes ( et des méthode peuvent en appeler d'autre ) :
::
    const app = new Vue({
        el: '#app',
        data: {
            favoriteColor: 'bleu'
        },
        computed: {
            label() {
                return ': ' + this.favoriteColor
            }
        },
        methods: {
            alertColor(color) {
                alert('Ma couleur préférée est ' + color)
            },
            changeColor() {
                console.log('Je veux changer ma couleur préférée !')
            }
        }
    })

Insertion de donnée dans les formulaire :
::
    <div id="app">
        <label for="un">Nom d'utilisateur</label>
        <input id="un" type="text" v-model="username" />
        <label for="pw">Mot de passe</label>
        <input id="pw" type="password" v-model="password" />
    </div>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                username: '',
                password: ''
            }
        })
    </script>

Vue avec le CLI
================
Installer vue CLI
::
    npm install -g @vue/cli
    # OR
    yarn global add @vue/cli
    #TEST
    vue --version

Créer un projet
::
    vue create my-first-vue-cli-app

Acceder a une interface local
::
    vue ui

Lancer un environnement de dev local
::
    npm run serve

Architecture de l'application
=============================

- node_module ( dépendance, gérer par yarn ou npm )
- public
- src ( 99% du temps )
    - Assets ( image, ressource )
    - Components
    - main.js ( option de configuration haut level
    -App.vue ( composants monofichier )
- .gitignore
- package.json ( avec serve pour l'env de developpement, et build )

Composant monofichier
=============================


.. _`Vue Docs`: https://fr.vuejs.org/v2/guide/
