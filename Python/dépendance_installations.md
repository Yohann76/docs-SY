## Installer python

installer python ( Windows ):

Telecharger Python 3.9 sur le Windows Store ( non vérifié )
ou sur le site officiel de Python

[downloads Python Windows](https://www.python.org/downloads/windows/)

installer pip:

Installer directement avec l'application windows Store

upgrade pip :
::

  $ pip install --upgrade pip


Dépendances et installation de librairie
========================================
::

    $ pip install pytest ( python testing ? )
    $ pip install Flask-Testing ( test pour flask )
    $ pip install xlrd ( sert a gerer l'extension excel )
    $ pip install flask_sqlalchemy ( ORM pour flask (
      [cours OC sur flask_sqlalchemy](https://openclassrooms.com/fr/courses/4425066-concevez-un-site-avec-flask/4525912-ajoutez-une-nouvelle-table-dans-la-base-de-donnees)
      )
    $ pip install brython ( faire tourner du python comme du js )
    $ pip install pygame ( Graphique et jeux)
    $ pip install svgwrite ( pour svg )
    $ pip install os, math ( gerer les os )
    $ pip install turtle ( module les dessin géométrique )

Module de Data Science
========================================

Module IA et machine learning
========================================
::

    $ pip install TensorFlow

Connaitre les modules installé avec python
==========================================
::

    $ pip freeze

Config de package python ( pour réinstallation complete )
==========================================================
::

    $ pip install alembic apipkg appdirs astroid atomicwrites attrs click colorama contextlib2 distlib execnet filelock Flask Flask-Migrate Flask-Script  Flask-SQLAlchemy Flask- Testing iniconfig isort itsdangerous Jinja2 lazy-object-proxy Mako MarkupSafe mccabe mock packaging path path.py pluggy psycopg2 py pylint pyparsing pytest pytest-shutil python-date util python-editor six SQLAlchemy svg.path svgwrite termcolor toml virtualenv Werkzeug wrapt xlrd
