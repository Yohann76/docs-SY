## Rsync ( Linux )

rsync est un outils installer de base sur Linux pour pouvoir synchroniser des repertoires.
Trés utile pour effectuer une backup de fichier ( .sql, .png et autre ).

Il est possible de faire la méme chose avec windows avec Xcopy

## Sauvegarde avec Rsync

    // sync deux repertoires, source et destination
    $ rsync -av  /source/yohann/Documents /destination/yohann/Documents/destination

    $ rsync -av /source /destination

    Paramétre :

    -a (copier tout les fichier et sous dossier, gére la récursivité)
    -v (verbose = details sur terminal)
    -- delete ( créer une copie conforme, efface dans la destination ce qui n'est pas dans la source )

Pour planifier déclanchement automatique de cette commande de sauvegarde :

    - Créer un fichier avec la commande rsync voulu
    - Renommer avec le .sh ( sauvegarde.sh )
    - Une fois le script effectuer, on va permettre l'execution : chmod +x /home/yohann/sauvegarde.sh
    - tache cron ( journalier à 20h ):    $ 00 20 * * * /home/yohann/sauvegarde.sh  // tout les jour à 20h = sauvegarde

## Récupération

pour le fichier sql, on peut injecter notre backup dans la base de données avec :

    $ source ;/var/backup/backup.sql (in the $mysql container)

## Xcopy ( Windows )
