Heroku : 
===================

Step : 
-------------------

https://devcenter.heroku.com/articles/deploying-symfony4


Commande : 
-------------------
::
    heroku create
    git remote-set-url heroku <lien obtenu précédement de git>
    heroku config:set DATABASE_URL=......
    Heroku open // ouvrir le lien de la page
    heroku ps:exec  // Se connencter a la machine // SSH 
    git push heroku master // pousher sur la branch heroku 
    
