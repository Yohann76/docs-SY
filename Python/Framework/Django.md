## Django

[Django  docs](https://docs.djangoproject.com/en/3.0/)

## Instalation



    $ python -m pip install Django // install Django avec Pip
    $ python -m django --version // voir la version de Django
    $ django-admin startproject mysite // Créer la base de code Django, nommé mysite
    $ cd mysite // pour lancer le server de dev
    $ python manage.py runserver // lancer le serveur de dev : http://127.0.0.1:8000/
    $ python manage.py runserver 8080 // pour changer le port du serveur de dev

Créer une App dans Django

    $ python manage.py startapp polls // création d'une App nommé "polls"// etre dans le méme repertoire que manage.py

## BDD :

réglages bdd dans settings.py pour information de connection,
également pour inclure l'application polls dans le projet ( toujours dans settings.py )

  INSTALLED_APPS = [
      'polls.apps.PollsConfig',
      'django.contrib.admin',
      'django.contrib.auth',
      'django.contrib.contenttypes',
      'django.contrib.sessions',
      'django.contrib.messages',
      'django.contrib.staticfiles',
  ]

Commande de database ( [Tuto docs Shell API](https://docs.djangoproject.com/fr/3.1/intro/tutorial02/) ) :

    $ python manage.py makemigrations polls // faire une migration de l'app polls ( dans container web docker )
    $ python manage.py migrate // appliquer les modifications à la base de données ( dans container web docker )
    $ python manage.py shell // avoir le shell API de Django ( pour communiquer avec la bases [Tuto docs Shell API](https://docs.djangoproject.com/fr/3.1/intro/tutorial02/))

## Notes :

    $ pip install psycopg2 // à installer pour pouvoir utiliser PostGreeSQL

Creation super user :


    $ python manage.py createsuperuser ( in docker web )
    -> saisir username : admin -> , email -> email , password -> password
    Interface de connexion directement disponibles dans /admin
