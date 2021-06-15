## RubyOnRails

`RoR guide`_

`RoR api dev`_

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


Ligne de commande rails ( une fois la gemme installé )
-------------------
::

  $ rails new blog // Créer un projet "blog" par default bdd = sqlite
  $ rails new blog --database=mysql // // Créer un projet "blog" avec bdd = mysql
  $ cd blog // rentrer dans le projet "blog"
  $ rails server // lancer le server de dev (http://localhost:3000)

.. _`RoR guide`: https://guides.rubyonrails.org/v5.2/
.. _`RoR api dev`: https://api.rubyonrails.org/
