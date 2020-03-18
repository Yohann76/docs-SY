API PLATEFORME : 
===================

Installation 
$ composer require api 

Api plateforme interface dispo sur /api 

Les annotations : 
-------------------

Définir comme ressource utilisable 
::

    /**
    * @ApiResource()
    */


    Définir Les droits : 
    * @ApiResource(
    *     attributes={"security"="is_granted('ROLE_USER')"}
    * )



Groups 
-------------------
::

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



Divers Annotation
-------------------


Autre
-------------------
Générer une docs : 
Generer avec le lien qui se trouve dans /api/ et faire pointer cette docs sur un lien 




