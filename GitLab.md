## Gitlab


[Gitlab](https://gitlab.com/)

Créer par Facebook en 2012.

Language de requéte :
Un langage de requête est un langage informatique utilisé pour accéder aux données d'une base de données ou d'autres systèmes d'information.

#### Commande


 installer git avec la commande :
 ::

    $ apt-get install git
    $ git config --global user.name "ThorAndCo" // connecter
    $ git config --global user.email thorandco@domaine.fr // connecter

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

Information :
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

Annuler un commit en particulier déjà pushé:
::

    git log
    git revert XXX
    git push

Gestion des branches :
::

  $ git checkout dev // Changer la branche courante
  $ git branch -v // Lister les branches
  $ git branch -d dev // Supprimer une branche ( dev )
  $ git checkout -b dev origin/dev // Récupérer une branche du dépôt git distant en local ( déconseiller )
  $ git merge dev // se rendre sur master, puis effectuer cette commande pour merger dev dans master

Commande diverse :
::

  $ git status // savoir le changement
  $ git add * // ajouter à l'index
  $ git shortlog -sn // Connaitre le nombre de commit git par utilisateur
  $ git branch dev // créer une branche dev
  $ git checkout -b dev // créer et switcher dessus
  $ git clone adresse_git_projet // Cloner un projet
  $ git push origin master // push ses commit sur la branch master



Avoir une variable privée pour gitlab :
::

 changer les variables dans le compte gitlab