## Heroku :


[Heroku docs](https://devcenter.heroku.com/categories/reference)

## Symfony : [Deployer avec SF4](https://devcenter.heroku.com/articles/deploying-symfony4)

  $ heroku create

  // for /public on symfony
  $ echo 'web: heroku-php-apache2 public/' > Procfile
  $ git add Procfile
  $ git commit -m "Heroku Procfile"

  $ heroku config:set APP_ENV=prod // change environment variable
  $ git push heroku master // push or deploy
  $ heroku open // open new windows

## Commande :


    $ heroku create
    $ git remote-set-url heroku <lien obtenu précédement de git>
    $ heroku config:set DATABASE_URL=......
    $ Heroku open // ouvrir le lien de la page
    $ heroku ps:exec  // Se connencter a la machine // SSH
    $ git push heroku master // pousher sur la branch heroku

## Divers :


    $ heroku ps:scale web=1 // vérifier qu'une instance est en cours
    $ heroku logs --tail // voir les logs en cours
    $ heroku restart // restart Heroku
    $ heroku run composer install // le prefixe heroku run permet d'executer sur le server heroku
    $ heroku config // voir la liste des config
