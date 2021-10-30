## ssl

Pour generer un certificat SSL et donc avoir HTTPS :

Vous devez passer par un organisme de certification.

## ssl avec let's encrypt (  [Certbot for Let's Encrypt](https://certbot.eff.org/lets-encrypt/ubuntubionic-nginx) )

    $ sudo snap install core; sudo snap refresh core
    $ sudo apt-get remove certbot
    $ sudo snap install --classic certbot
    $ sudo ln -s /snap/bin/certbot /usr/bin/certbot
    $ sudo certbot --nginx
    $ sudo certbot renew --dry-run
