## Tache Cron

Syntaxe :

    mm hh jj MMM JJJ [user] tâche > log

     $ crontab -l // lister
     $ crontab -e // editer
     $  crontab -r // supprimer tous

     $ export VISUAL=nano; crontab -e // paramettrer l'ouverture des taches cron avec nano

Tous les jour a 22h :

    $ 00 22 * * * /root/scripts/sauvegarde.sh >> sauvegarde.log

toute les 6 heures :

    $ 00 */6 * * * /root/scripts/synchronisation-ftp.sh


toute les heures :

    $ 00 */1 * * * /usr/sbin/ntpdate fr.pool.ntp.org

toute les minute seulement le lundi :

    $ * * * * 1 /root/script/commandes-du-lundi.sh


22 decembre a 00h15 ( une fois par an ) :

    $ 15 00 25 12 * echo "Le père Noël est passé !"


$ 00 22 * * * /root/scripts/sauvegarde.sh >> /root/scripts/sauvegarde.log // mettre les logs
