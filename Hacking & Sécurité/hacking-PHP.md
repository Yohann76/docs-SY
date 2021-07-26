### Injection SQL

Il s'agit de modifier une requete SQL a l'issu d'un formulaire. le log des variables POST permet de visualiser une requete SQL, mais souvent il n'y a pas de visualisation possible.

Ajouter une entrée valide à l'infini sur le login, pour se connecter avec un mot de passe bidon.

  ' OR 1=1 OR 1= '

Protection : Mettre des antiSlash devant les guillemets au traitement, ou echapper les guillemets, traiter les variable POST plus serieusement !
