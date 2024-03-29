## Flask

Flask est un micro framework très minimaliste et leger, concu pour developper des application rappidement.

Demmarrer avec flask en 7 lignes

    from flask import Flask

    app = Flask(__name__)
    @app.route('/')
    def index():
        return "Hello world !"

    if __name__ == "__main__":
        app.run()

Python créer un environnement a l'adresse localhost:5000

## installation

Necessite pip

flask

    $ pip install flask

virtualenv ( pas obligatoire ,
pour géré plusieurs projets avec des variables différentes )


    $ pip install virtualenv
    $ virtualenv -p python3 env // créer un environnement

## Obtenir l'environnement ( simuler le site et démarrer le serveur )

1. Terminal : Aller dans le repertoire du site
2. Terminal : python views.py
3. Se rendre sur l'adresse indiqué ( souvent http://127.0.0.1:5000/ )
4. Naviguer sur le site et observer le terminal

## Structure

- Static : CSS/images:script
- Templates : Fichiers HTML
- Tests : ranger les tests
- views.py : Contient les diférentes routes
- config.py : variable de configuration
- Les controllers peuvent êtres inclus en annexe ( utils.py,... ) et être importé sur views.py

Console Flask

lancer la console flask


    $ set FLASK_APP=run.py
    $ set FLASK_APP=run.py flask init_db  // avec une méthode d'initialisation

puis

    $ flask shell

## Base de donnée SQLlite

1. Connecter la base de donnée :
Comment connecter la base de donnée ?

Il faudra installer Sqlite, et mettre le dossier sqllite dans C:\sqlite, pusi définir ce dossier comme variable d'environnement. Voici ensuite quelques commande sur la base de donnée :


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

## Les tests

lancer un test :

    $ pytest app/tests/test_functionnal.py

librairie requise :
- Selenium
- flask-testing
- pytest

Les tests ont besoin de __init__.py, config.py dans le dossier de test


BDD postres SQL

- models.py pour implementer la classe qui représente les tables
- manage.py pour acceder a a la base

    #from flask import Flask
    from flask_script import Manager
    from flask_migrate import Migrate, MigrateCommand
    from app import app, db

    manager = Manager(app)
    migrate = Migrate(app, db)

    manager.add_command('db', MigrateCommand)

    #if __name__ == '__main__':
        #manager.run()

## Commande :

    $ python manage.py db init ( initialiser la base )
    $ python manage.py db migrate ( faire une migration )

## Route avec flask

    @app.route("/greeting")
    def greeting():
      return {"greeting": "Hello from Flask API"}

    @app.route("/addLabel/<nb1>/<nb2>")
    def addLabel(nb1,nb2):
      return addLabelAPI(escape(nb1),escape(nb2))

## API avec flask ( /api/ )

dans api/app.py

    from flask import Flask
    from flask_cors import CORS
    from apiFunction import addLabelAPI, addRecordAPI, createDataAPI
    from markupsafe import escape
    import models
    from models import db, Label, Record

    app = Flask(__name__)
    app.config.from_object('config')
    app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False
    CORS(app)
    models.db.init_app(app)

    @app.route("/")
    def home():
        return {"home": "Welcome to Flask API"}

    # Route : /addLabel/{title}/{node1}/{node2}/{functionNumber}/{column}
    @app.route("/addLabel/<string:title>/<string:node1>/<string:node2>/<int:functionNumber>/<int:column>", methods=['GET'])
    def addLabel(title,node1,node2,functionNumber,column):
        # try this route: addLabel/loremIpsum/BR45/CV10/1/1
        return addLabelAPI(str(title), str(node1), str(node2), int(functionNumber), int(column))

Définition de addLabelAPI dans /api/apiFunction.py

    import math
    from models import db, Label, Record

    #return addLabelAPI(escape(title),escape(node1),escape(node2),escape(functionNumber), escape(column))
    def addLabelAPI(title,node1,node2,functionNumber,column):
        #db.create_all()
        Label1 = Label(title=title, node1=node1, node2=node2, functionNumber=functionNumber, column=column)
        db.session.add(Label1)
        db.session.commit()
        return {"labelStatus": "added in database"}

other
