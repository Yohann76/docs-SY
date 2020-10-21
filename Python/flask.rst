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
