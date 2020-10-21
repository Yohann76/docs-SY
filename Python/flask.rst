Flask
======

Flask est un micro framework très minimaliste et très leger, concu pour developper des application rappidement.

Demmarrer avec flask en 7 lignes
::
  from flask import Flask

  app = Flask(__name__)
  @app.route('/')
  def index():
      return "Hello world !"

  if __name__ == "__main__":
      app.run()
      
Python crée un environnement a l'adresse localhost:5000

installation 
===========

flask
::
  pip install flask
  
virtualenv 
::
  pip install virtualenv
  virtualenv -p python3 env // créer un environnement 
  
Structure
===========

Static : CSS/images:script
Templates : Fichiers HTML
Tests : ranger les tests
views.py : Contient les diférentes routes
config.py : variable de configuration
