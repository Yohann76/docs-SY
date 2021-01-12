Vuex
=============================

Vuex est un magasin centraliser pour stocker toute les data de l'applications ( dans Vue )
Nous pouvons facilement sotcker les data et les récupéré.

Instalation de vuex avec VueCLI ( `OC instalation Vuex`_ ) :
::

  $ vue add vuex

Cela modifie de main.js et crée un store.js dans src

Récupéré des données avec Vuex ( `OC récupération données Vuex`_ ) :
::

  <template>
    <p>La date stockée dans Vuex est le {{ $store.state.day }}-{{ $store.state.month }}-{{ $store.state.year }}.</p>
  </template>


.. _`OC instalation Vuex`: https://openclassrooms.com/fr/courses/6390311-creez-une-application-web-avec-vue-js/6869761-creez-un-data-store-centralise-avec-vuex
.. _`OC récupération données Vuex`: https://openclassrooms.com/fr/courses/6390311-creez-une-application-web-avec-vue-js/6870051-recuperez-des-donnees-depuis-vuex
