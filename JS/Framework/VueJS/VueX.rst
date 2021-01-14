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


Définir le state dans store.js  ( Grafikart tuto ( `Grafikart tutoVuex`_ ) :
=============================
::

  import Vue from 'vue'
  import Vuex from 'vuex'

  Vue.use(Vuex)

  const state = {
    diagram: [{
      name: 'Diagram',
    }]
  }
  export default new Vuex.Store({
    state: state,
    mutations: {
    },
    actions: {
    },
    modules: {
    }
  })

Le State est visible dans l'extension Chrome VueTools

Les mutation ( fonction pour par exemple ajouer des choses )
=============================
::

  import Vue from 'vue'
  import Vuex from 'vuex'

  Vue.use(Vuex)

  const state = {
    diagram: [{
      name: 'Diagram',
    }]
  }

  const mutations = {
    ADD_FUNCTION :(state, name) => {
      state.diagram.push ({
        name: name,
        number : false
      })
    }
  }

  let store = new Vuex.Store({
    state: state,
    mutations: mutations,
    actions: {
    },
    modules: {
    }
  })

  global.store = store

  export default store

Nous pouvons désormais accéder au state du store via la console avec store.state ( avec les deux derniére ligne )
Une mutation peux etre effectuer et tester en ligne de commande dans la console avec : store.commit('ADD_FUNCTION', 'nametest'),
nous avons ensuite une mutation qui modifie le state dans l'extension vueTools

Utiliser et acceder au store depuis des component, qui ont un lien de parenté, ou non
=============================

Les Getter
=============================
dans le component
::

  import store from "../store";
  import Vuex from 'vuex';
  ...

  computed: {
    ...Vuex.mapGetters(['diagram']),
  }

dans le store.js
::

  // use in component for get data
  const getters = {
    diagram: state => state.diagram
    // other getter
  }
  let store = new Vuex.Store({
    state: state,
    mutations: mutations,
    getters:getters,
    actions: {
    },
    modules: {
    }
  })

  global.store = store
  export default store

.. _`OC instalation Vuex`: https://openclassrooms.com/fr/courses/6390311-creez-une-application-web-avec-vue-js/6869761-creez-un-data-store-centralise-avec-vuex
.. _`OC récupération données Vuex`: https://openclassrooms.com/fr/courses/6390311-creez-une-application-web-avec-vue-js/6870051-recuperez-des-donnees-depuis-vuex
.. _`Grafikart tutoVuex`: https://www.youtube.com/watch?v=OjM7hzcdBrs&t=1003s&ab_channel=Grafikart.fr
