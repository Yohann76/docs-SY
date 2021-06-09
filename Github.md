
## Github organization ( compte partagé )

`Github organisation`_

2 organisation
- SYD Tools

#### Github

`Github Doc`_
`Github API`_

S'identifier à git
-------------------

Commande pour s'identifier:
::
     $ git config --global user.name "Username"
     $ git config --global user.email "mail"

Ajouté un repository a github :
-------------------

Créer le repo sur la plateforme, upload les fichiers, et cloner le projet
::

   $ git clone LienDuProjet

Créer le repo sur la plateforme SANS README.txt et pusher en cli
pour le push la première fois, enlever le .git a la racine si il y a
git init
::

   git add .
   git status ( pour voir les fichier add a l'index )
   git commit -m "message"
   git remote add origin https://github.com/Yohann76/BileMo_B2B_API
   git push -u origin master ( demande UserName et mots de passe )

ou cliquer sur le repo et copier les commandes, avec https


Faire un commit :
-------------------
::

   git add * ( pour ajouter tout a l'index, sauf ce qui est exclus dans .gitignore )
   git status
   git commit -m "Message du commit"  // -m = commentaire du commit
   git push origin master

Corriger le message du dernier commit :
::

   git commit --amend -m "Nom de commit corrigé"

mais attention, vous ne pouvez modifier ce message que si vous n'avez pas encore pushé votre commit sur l'origine !

revenir sur un commit précédent  :
::

   git checkout SHADuCommit ( 5e78e8e389e28cf9ea91708eb37abfd975ffce31 par exemple )

Créer un commit qui fait l'inverse du précédent ( attention cela crée un nouveau commit )  :
::

   git revert SHADuCommit

Annuler tout les changements lorsqu'un nouveau commit n'a pas été fait :
::
   git reset
   git reset --hard‌


Voir la liste des commit effectué
::
   git log

Désindexer un fichier ajouté a l'index pour un commit
::

    git restore --staged <fichier>...

Synchroniser une branche avec une autre branche
::
   git pull origin master ou dev...


Commande divers :
-------------------
::

   $ git branch // voir la branche actuelle et toutes les branch
   $ git branch mon-test // Créer une nouvelle branch nommé "mon-test"
   $ git checkout mon-test // pour changer de branch, se positionner sur une branch
   $ git branch -D mon-test // Supprimer une branche
   $ git branch -b mon-test // Créer une branche et aller dessus directement
   $ git remote show origin // voir la liste des branches distantes
   $ git merge brancheB // La B rentre dans A ou master
   $ git pull origin master // Récuperer le code de master, copier une branch
   $ git reset monfichieroudossier // Retirer un fichier ou dossier de l'index aprés un git add *
   $ git rev-list --count HEAD // compter le nombre de commit sur la branch actuelle ls

( voir pour git push origin master aprés pour effectuer la merge )
( ou faire une demande de pull request sur git )

Contribution Open Source :
-------------------
1. Créer une issue pour ajouter ou corriger
2. créer la branch associé
3. bosser sur la branche
4. Commmit sur la branch
5. Créer une pull request
6. Attendre que une personne regarde et merge la PR
7. celui qui merge supprime la branche et close l'issue


.. _`Github organisation`: https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/about-organizations
.. _`Github Doc`: https://help.github.com/en
.. _`Github API`: https://developer.github.com/v3/
