## Dolibar

CMS pour installer un ERP sur un server

[Dolibarr github](https://github.com/Dolibarr/dolibarr)

## Instalation sur VPS OVH ubuntu

Dans le VPS :

    $ sudo git clone https://github.com/Dolibarr/dolibarr.git

Donc première chose à faire il faut ajouter un champ CNAME à vos résolutions DNS, afin que sub.toto.me pointe vers toto.me

### pour apache :

 Il faut éditer le fichiers /etc/apache2/sites-available/default et y ajouter les lignes suivantes :

    <VirtualHost *:80>
     DocumentRoot /home/toto/www/sub
     ServerName sub.toto.me
    </VirtualHost>

 Il suffit de redémarrer Apache avec un :

    $ sudo /etc/init.d/apache2 restart
    $ sudo /etc/init.d/apache2 nginx



Télécharger Dolibarr.
Créer le dossier documents de Dolibarr.
Extraire l'archive de Dolibarr.
Installer Dolibarr
Configurer la base de données.
Terminer la configuration de Dolibarr.
Créer le fichier install.lock.
Restreindre l'accès en écriture du Serveur Web au fichier conf.php.
