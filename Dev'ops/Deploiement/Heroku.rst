Heroku : 
===================

`Heroku docs <https://devcenter.heroku.com/categories/reference>`_

Step : 
-------------------
`Deployer avec SF4 <https://devcenter.heroku.com/articles/deploying-symfony4>`_


Commande : 
-------------------
::
    heroku create
    git remote-set-url heroku <lien obtenu précédement de git>
    heroku config:set DATABASE_URL=......
    Heroku open // ouvrir le lien de la page
    heroku ps:exec  // Se connencter a la machine // SSH 
    git push heroku master // pousher sur la branch heroku 
    
