## Sylius

Instalation :

[Sylius docs install](https://docs.sylius.com/en/latest/getting-started-with-sylius/installation.html)

    $ composer create-project sylius/sylius-standard MyFirstShop
    $ cd MyFirstShop

    - create .env.local
    $ php bin/console d:d:c
    $ php bin/console d:s:u --force

    $ php bin/console sylius:install
    ( currency : USD or ??? )

    $ yarn install
    $ yarn build

    $ symfony serve
    $ open http://127.0.0.1:8000/admin or http://127.0.0.1:8001/admin
