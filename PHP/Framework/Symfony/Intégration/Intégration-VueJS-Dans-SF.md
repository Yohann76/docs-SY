## VueJS Dans SF


[Tuto pour vueJS/Symfony](https://nicolasfz-code.medium.com/symfony-et-vue-js-partie-1-installation-et-configuration-b986849e0ba)

## Installer Symfony et WebPack :

    $ symfony new --full MyVueProject
    $ composer require symfony/webpack-encore-bundle
    $ yarn install


    $ yarn encore dev // pour compiler en dev
    $ yarn encore production // pour compiler en prod

    $ symfony server:start

## Installer vueJS avec Symfony et Webpack


ajouter au template base au lieu de la balise body :

    {% verbatim %}
    <div id="app">
        {{ message }}
    </div>
    {% endverbatim %}

dans le assets/app.js :

    import Vue from 'vue'

    new Vue({
      el: '#app',
      data: {
          message: 'Hello Vue!'
      }
    })

dans webpack encore ajouter :

    // Activation de Vue.js
    .enableVueLoader()

puis :

    $ yarn add vue vue-loader vue-template-compiler --dev
    $ yarn encore dev

    Go symfony url /localhost pour tester, "Hello vue!"" doit apparaitre
