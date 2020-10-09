Gitlab
===================

`Gitlab`_

Créer par Facebook en 2012.

Language de requéte : 
Un langage de requête est un langage informatique utilisé pour accéder aux données d'une base de données ou d'autres systèmes d'information.

Commande
-------------------

 installer git avec la commande : 
 ::

    apt-get install git

Se connecter : 
::

    git config --global user.name "ThorAndCo"
    git config --global user.email thorandco@domaine.fr

Créer un nouveau projet vide sur un dépot git vide : 
::

    cd /home/git
    mkdir monprojet
    cd monprojet
    git init
    touch README
    git add README
    git commit -m 'Premier Commit'
    git remote add origin git.domaine.fr/thorandco/monprojet.git
    git push -u origin master

 Initialiser un projet git depuis un dépôt existant
 ::

    cd /home/git
    mkdir monprojet
    cd monprojet
    git init
    git remote add git.domaine.fr/thorandco/monprojet.git
    git pull -u origin master

Commiter sur le dépôt git local : 
::

    git commit --amend -m "Ajout du fichier monfichier.txt pour le projet"

Voir l’historique des commits :
::

    git log

Annuler un commit : 
::

   git reset HEAD 
   git reset HEAD nomdufichier.txt ( sur un fichier précis ) 


Récupérer les sources du dépôt distants: 
::

    git fetch
    git pull origin master

Pusher ses commit sur le dépot distant:
::

    git push origin master

Annuler un commit en particulier déjà pushé:
::

    git log
    git revert XXX
    git push


Les branches :


Créer un branche dev :
::

    git branch dev
    git checkout -b dev ( créer et switcher dessus ) 

Lister les branches : 
::

    git branch -v

Changer la branche courante:
::

    git checkout dev

Supprimer une branche :
::

    git branch -d dev

Récupérer une branche du dépôt git distant en local :
::

    git checkout -b dev origin/dev

Merger (fusionner) une branche avec une autre
Par exemple, pour fusionner la branche « dev» avec la branche « master » :
::

    git checkout master
    git merge dev

Statistiques
Connaitre le nombre de commit git par utilisateur :
::

    git shortlog -sn
 

.. _`Gitlab`: https://gitlab.com/