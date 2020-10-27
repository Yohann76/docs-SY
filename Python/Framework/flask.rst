Flask
======

Flask est un micro framework très minimaliste et leger, concu pour developper des application rappidement.

Demmarrer avec flask en 7 lignes
::
  from flask import Flask

  app = Flask(__name__)
  @app.route('/')
  def index():
      return "Hello world !"

  if __name__ == "__main__":
      app.run()

Python créer un environnement a l'adresse localhost:5000

installation
===========

Necessite pip ( dans machine virtuel Debian sur Windows )

flask
::
  pip install flask

virtualenv
::
  pip install virtualenv
  virtualenv -p python3 env // créer un environnement

Obtenir l'environnement
===========
1. Terminal : Aller dans le repertoire du site
2. Terminal : python views.py
3. Se rendre sur l'adresse indiqué ( souvent http://127.0.0.1:5000/ )
4. Naviguer sur le site et observer le terminal

Structure
===========

- Static : CSS/images:script
- Templates : Fichiers HTML
- Tests : ranger les tests
- views.py : Contient les diférentes routes
- config.py : variable de configuration
- Les controllers peuvent êtres inclus en annexe ( utils.py,... ) et être importé sur views.py


Console Flask
==============

lancer la console flask
::
  set FLASK_APP=run.py
  set FLASK_APP=run.py flask init_db  // avec une méthode d'initialisation
puis
::
  flask shell

Base de donnée SQLlite
=======================

1. Connecter la base de donnée :
Comment connecter la base de donnée ?

Il faudra installer Sqlite, et mettre le dossier sqllite dans C:\sqlite, pusi définir ce dossier comme variable d'environnement. Voici ensuite quelques commande sur la base de donnée :
::
  from fbapp.models import db, Content

  db.session.add(Content("What's your favorite scary movie?", 0))
  db.session.commit()
  Content.query.all()
  // affiche un array de 1
  content = Content.query.get(1)
  db.session.delete(content)
  db.session.commit()
  Content.query.all()
  // affiche un tableau vide

Les tests
=========

lancer un test :
::
  pytest app/tests/test_functionnal.py

librairie requise :
- Selenium
- flask-testing
- pytest

Les tests ont besoin de __init__.py, config.py dans le dossier de test
