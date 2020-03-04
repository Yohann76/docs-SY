.. index::
   single: Github; Github

Github
===================
`Github Doc <https://help.github.com/en>`_
`Github API <https://developer.github.com/v3/>`_

S'identifier à git 
-------------------

Commande pour s'identifier::
     $ git config --global user.name "Username"
     $ git config --global user.email "mail"
  
Ajouté un repository a github : 
-------------------

Créer le repo sur la plateforme, upload les fichiers, et cloner le projet 
$git clone LienDuProjet

Créer le repo sur la plateforme SANS README.txt et pusher en cli
pour le push la première fois, enlever le .git a la racine si il y a
git init
git add . 
git status ( pour voir les fichier add a l'index ) 
git commit -m "message" 
git remote add origin https://github.com/Yohann76/BileMo_B2B_API
git push -u origin master ( demande UserName et mots de passe ) 

ou cliquer sur le repo et copier les commandes, avec https 


Faire un commit : 
-------------------

git add * ( pour ajouter tout a l'index, sauf ce qui est exclus dans .gitignore ) 
git status
git commit -m "Message du commit"  // -m = commentaire du commit
git push origin master


Récupérez des modification 
-------------------

Pour avoir la dernière version du repo en ligne sur le local  ( synchroniser ) 
$ git pull origin master // ( pour être à jour ) 

Créer une branche : 
-------------------

$ git branch // voir la branche actuelle et toutes les branch 
$ git branch mon-test // Créer une nouvelle branch nommé "mon-test" 
$ git checkout mon-test // pour changer de branch 

Supprimer une branche ?? 

Fusionnez des branches :
-------------------

Se positionner sur master 
$ git checkout brancheA // (ou master)
$ git merge brancheB // La B rentre dans A ou master 
( voir pour git push origin master aprés pour effectuer la merge ) 
( ou faire une demande de pull request sur git ) 

Contribution :
-------------------
1. Créer une issue pour ajouter ou corriger
2. créer la branch associé
3. bosser sur la branche
4. Commmit sur la branch 
5. Créer une pull request 
6. Attendre que une personne regarde et merge la PR 
7. celui qui merge supprime la branche et close l'issue 




