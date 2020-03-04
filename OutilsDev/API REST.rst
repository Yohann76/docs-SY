API REST


Les différente API et leurs requêtes :
Facebook ( Lien ici )
Github
Google
Nasa
Gmail
Paypal
L'authentification par API
Créer une API REST pour son projet  :
Méthode http :
6 contraintes de REST :
Gérer avec API PLATEFORME :
Les annotations :
Gérer avec PostMan :


Les différente API et leurs requêtes : 
Facebook ( Lien ici ) 
Github
Google
Nasa
Gmail 
Paypal 
L'authentification par API 



Créer une API REST pour son projet  : 
Méthode http : 
GET : Permet de récupérer une ou plusieurs ressource.
POST : Permet de créer une nouvelle ressource.
PUT : Permet de remplacer une ressource existante.
PATCH : Permet de remplacer partiellement une ressource existante.
DELETE : Permet la suppression d’une ressource.

6 contraintes de REST : 
Client-serveur
Sans état
Avec mise en cache
En couche
Avec code à la demande ( facultative ) 
A interface uniforme 

Modèle de richardson : Ici
Code serveur : 
201 : Validation
404 : page non trouver
403 : 

Gérer avec API PLATEFORME : 
Installation 
$ composer require api 
Api plateforme interface dispo sur /api 

Les annotations : 

Définir comme ressource utilisable 
/**
* @ApiResource()
*/


Définir Les droits : 
* @ApiResource(
*     attributes={"security"="is_granted('ROLE_USER')"}
* )



Groups 

use Symfony\Component\Serializer\Annotation\Groups;

* @ApiResource(
*     collectionOperations={
*     "get"={
*             "normalization_context"={"groups"={"api"}}
*         },
*     "post"
*      },
*     itemOperations={
*     "get"={
*             "normalization_context"={"groups"={"api"}}
*         },
*     "post"={
*          "method"="POST",
*          "method"="DELETE"
*          }
*     }
* )












Gérer avec PostMan : 



