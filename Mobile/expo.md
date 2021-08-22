## Expo

Info :
-------------------
Expo est un utilitaire pour la gestion des CRNA. Une application expo facilite le développement mobile avec javascript.
En revanche, expo et les CRNA ne permettent pas d'utiliser des composants natifs, pour cela il faudra ejecter l'application. C'est a dire enlever la couche
expo, et tester son application avec un port USB ( + SDK + AVD + Android studio ).

Ejecter une application est irréversible, mais cela est courant a la fin de projet, lors d'utilisation de composants natifs.


Initialisation d'une application expo :
-------------------

A utiliser avec l'application expo

    expo init MonProjet
    npm start


Build une application expo :
----------------------------

    expo build:android
    expo build:ios

Expo dispose d'un serveur dédié pour build les application et télécharger les APK, il faudra s'inscrire sur le site expo pour avoir un dashboard
des applications ainsi que leurs états.
