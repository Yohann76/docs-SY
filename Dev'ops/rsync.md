## Rsync ( Linux )

rsync est un outils de sauvegarde et de synchronisation trés puissant installer de base sur Linux pour pouvoir synchroniser des repertoires.
Trés utile pour effectuer une backup de fichier ( .sql, .png et autre ).

Il est possible de faire la méme chose avec windows avec Xcopy

## Sauvegarde avec Rsync (de base dans linux)

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

## Xcopy (Windows)

[Xcopy Docs](https://docs.microsoft.com/fr-fr/windows-server/administration/windows-commands/xcopy)

Il existe une solution de synchronisation sur windows. c'est Xcopy.

    $ Xcopy <Source> [<Destination>] [/w] [/p] [/c] [/v] [/q] [/f] [/l] [/g] [/d [:MM-DD-YYYY]] [/u] [/i] [/s [/e]] [/t] [/k] [/r] [/h] [{/a | /m}] [/n] [/o] [/x]
    [/exclude:FileName1[+[FileName2]][+[FileName3]]] [{/y | /-y}] [/z] [/b] [/j]

## Rclone  (outils pour linux à installer)

Rclone est comme rsync, mais n'est pas de base sur linux. cependant il offrent une grande capacité de synchronisation avec S3, Google Cloud, et plein d'autre plateforme.
[Tuto Korben Rclone](https://korben.info/rclone-rsync-cloud-dropbox-amazon-s3-google-drive-hubic-backblaze-etc.html?fbclid=IwAR0V6-9DYU2gx485Tg99XO9jZ6Mz1dk74fE20jKj6FOnWEsLD4QhDW0ZbhU)



# install Rclone manualy in your serve : https://computerz.solutions/backup-rclone/#Installation_de_Rclone

curl https://rclone.org/install.sh | sudo bash
rclone config ( N - drive - 16 -  -  - 3 -  -  - n - n  )
go to the url in commander
past verification code in commander
rclone ls drive:/privanciel-save

# Exemple command Rclone :

    sudo rclone copy /var/www/html/Privanciel/var/backup/ drive:/privanciel-save/app-privanciel/database/    
    sudo rclone copy /var/www/html/Privanciel/public/organization/img/logo drive:/privanciel-save/app-privanciel/img

    sudo rclone sync /source :drive:/folderinclouddrive // synchroniser la source et la destination ( exactement la méme chose de chaque coté )
    sudo rclone copy /source :drive:/folderinclouddrive // Copie la source dans la destination ( seul les element qui change )
