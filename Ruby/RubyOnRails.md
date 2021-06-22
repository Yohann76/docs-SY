## RubyOnRails

[RoR guide](https://guides.rubyonrails.org/v5.2/)
[RoR api dev](https://api.rubyonrails.org/)

Ruby on Rails, également appelé RoR ou Rails, est un framework web libre écrit en Ruby. Il suit le motif de conception modèle-vue-contrôleur (MVC).
Il propose une structure qui permet de développer rapidement et intuitivement. Cependant, il impose un grand niveau d'abstraction dans la programmation
qui apporte en contrepartie l'économie d'écrire soi-même la plupart des routines obligatoires d'une application web.

Instalation & pré-requis
-------------------
::

  $ ruby --version // savoir la version
  $ gem install rails // Installer Rails avec une gemme de ruby
  $ rails --version // savoir la version de rails installer

  $ sqlite3 --version
  $ node --version
  $ yarn --version


Création de page
-------------------
::

  config/route.rb
    get '/salut', to:'pages#salut'


  app/Controllers ( à créer )
    pages_controller.rb
    class PagesController < ApplicationController
      def salut
      end
    end

  App/Views
    pages ( créer dossier )
      salut.html.erb ( créer dans pages )

  App/View/Layouts/applications ( base du html )


Ligne de commande rails ( une fois la gemme rails installé )
-------------------
::

  $ rails new blog // Créer un projet "blog" par default bdd = sqlite
  $ rails new blog --database=mysql // // Créer un projet "blog" avec bdd = mysql
  $ cd blog // rentrer dans le projet "blog"
  $ rails server // lancer le server de dev (http://localhost:3000)
  $ rails console // pour lancer la console rails

Commande dans la console ( rails c ou rails console )
-------------------
::

  $ rails console --sandbox // lancer la console en mode bac à sable, pour qu'une fois sortie de la console les modif sont pas persisté
  $ Post.find(1) // chercher dans la base de donnée dans la table post l'id 1
  $ p = Post.find(1) // stocker dans une variable la requete
  $ p.name // pour récupérer le nom
  $ p.content = "hello ça va" // pour modifier
  $ p.save // persister le changement en bdd
  $ p.destroy // supprimer un changement en bdd ( mais toujours existant en bdd )

  // ajouter une ligne
  $ p = Post.new
  $ p.title = "salut"
  $ p.save
  $ p // voir la variable qu'on à créer

  // récupérer des données
  $ Post.first // recupérer le premier
  $ Post.last // recupérer le dernier
  $ Post.count // Compter le nombre de ligne
  $ Post.all // tout récupérer p = Post.all, p[0], P[1]..
  $ Post.where(name:'salut')
  $ Post.limit(1)


Base de données
-------------------
::

  $ rails g migration CreatePosts title:string content:text // generer la migration d'une table  Posts  avec title, content...
  $ rails db:migrate // appliquer une migration à la base de données
  $ rails db:rollback // inverser la derniére migration effectué
  $ rails g migration RenamePostTitleToName // donner un nom à une migration, utile pour modifier les choses


Connexion Database SQL sur VSCode
-------------------
   1. Installer l'extension SqLite
   2. Ouvrir la palette de commandes ( ctrl + shift + p)
   3. sellectionnez SQLite : open database
   4. choisir development.sqlite3
   ou dans base de données, choisir sqlite connection et prendre le fichier qui se trouve dans db/migrate/development.sqlite3
