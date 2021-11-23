## Symfony traduction


[Symfony traduction docs ](https://symfony.com/doc/current/translation.html)

    composer require symfony/translation


- Définir la langue de base dans config/packages/translation


## Les traductions :


Faire une traduction dans le controller

    $translated = $translator->trans('Symfony is great');


Faire une traduction de texte static dans twig :

    {% trans %}Hello {% endtrans %}


Pour traduire dans les bases de données :

[Symfony Doctrine Extension translatable](https://github.com/doctrine-extensions/DoctrineExtensions/blob/main/doc/translatable.md)
[Symfony KnpLabs Doctrine behavior](https://github.com/KnpLabs/DoctrineBehaviors)



-  Une fois toute les traductions faites, il est possible de generer un fichier xlf ( editable avec le logiciel poedit )

    $ php bin/console translation:update --force fr // fr ou en ou autre langue // commande pour generer un fichier, créer un nouveau fichier, ecrase pas l'ancien 

## Traducteur Externe

Il est possible d'avoir des traducteur externe comme Crowdin ou Lokalise.
Une configuration simple de l'api est envisageable. C'est une fonctionnalité expérimental.

L'interet est de pouvoir envoyer directement des choses à traduire ou récuperé via :4

  $ php bin/console translation:push loco --force
  $ php bin/console translation:push loco --locales fr --domain validators
  $ php bin/console translation:push loco --delete-missing --locales fr --domain validators
