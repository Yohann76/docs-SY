API REST
===================

Créer une API REST pour son projet  :
Méthode https :
GET : Permet de récupérer une ou plusieurs ressource.
POST : Permet de créer une nouvelle ressource.
PUT : Permet de remplacer une ressource existante.
PATCH : Permet de remplacer partiellement une ressource existante.
DELETE : Permet la suppression d’une ressource.

6 contraintes de REST :
-------------------

Client-serveur
Sans état
Avec mise en cache
En couche
Avec code à la demande ( facultative )
A interface uniforme

Code serveur :
-------------------


  200 : Requête traitée avec succès
  201 : Validation
  404 : page non trouver
  401 : Accès à la ressource refusé
  500 : Erreur interne du serveur


API Utilisable
===================


Facebook
-------------------
`Facebook API Docs`_

TODO : Se connecter via auth ?

Github
-------------------
`Github API Docs`_

TODO : Se connecter via auth ?
TODO : Récupérer le contenu d'un repository ( requete )

Google
-------------------
`Google API Docs`_

TODO : Se connecter via auth ?


Paypal
-------------------
`Paypal API Docs`_

TODO : Gestion d'un service de paiment

Nasa
-------------------
`Nasa API Docs`_

TODO : Récupérer des informations sur une planete ( requete )


.. _`Nasa API Docs`: https://api.nasa.gov/
.. _`Paypal API Docs`: https://api.nasa.gov/
.. _`Google API Docs`: https://developers.google.com/apis-explorer
.. _`Github API Docs`: https://developer.github.com/v3/
.. _`Facebook API Docs`: https://developer.github.com/v3/
