## domaine

Un nom de domaine redirige sur une adresse ip. Nous pouvons lié n'importe quels domaine à n'importe quels adresse ip.
Adresse IP et Serveur ne sont pas obligatoirement avec le méme hebergeur.

Pour lié un ndd à un serveur, il faut modifier la zone DNS :  l'entre de type de champ "A" et mettre une cible en IP

## Nom de domaine sur OVH :

Pour configurer un sous non de domaine sur OVH

Ensuite pour le lié à un server :
Aller dans la zone dns du domaine , modifier l'entre de type de champ "A" et mettre une cible en IP

voir si c'est le bon propriétaire du domaine :
DNS  ownercheck.yohanndurand.fr. avec la valeur texte "1c53caf5" ( fournis par OVH quand sur le vps on veux ajouter le ndd dans zone dns )

## Les sous domaine :

Se rendre dans la partie "nom de domaines"

Ajouter une entré ->
Type de champ : CNAME
Domaine : sousdomaine.mondomaine.fr
cible :mondomaine.fr. ( le point final est important )

Ensuite pour pusher correctement avec ansible :

Modifier la variable server_name dans ansible/vars :
server_name:


    bilemo.yohanndurand.fr

Ensuite modifier le symfony.conf pour que nginx puisse avoir les bonnes info :


    server_name {{ server_name }} www.{{ server_name }};
        root {{ symfony_web_dir }};

        location / {
            # try to serve file directly, fallback to index.php
            try_files $uri /index.php$is_args$args;
            autoindex on;
            autoindex_exact_size off;
        }


Nous pouvons donc faire une architecture multi-site comme celle-ci :

Portfolio ( server name : yohanndurand.fr ( A vérifier )
Sous ndd sur Bilemo ( server name : bilemo.yohanndurand.fr )
Sous ndd sur Snowtricks ( server name : snowtricks.yohanndurand.fr )
