## Tache Cron


Si non installé par default :

    $ apt-get install cron


Syntaxe :

    mm hh jj MM (day of month (1 - 31))  JJJ ( day of week (0 - 6) )   [user] tâche > log


mm : minutes (00-59).
hh : heures (00-23) .
jj : jour du mois (01-31).
MMM : mois (01-12 ou abréviation anglaise sur trois lettres : jan, feb, mar, apr, may, jun, jul, aug, sep, oct, nov, dec).
JJJ : jour de la semaine (1-7 ou abréviation anglaise sur trois lettres : mon, tue, wed, thu, fri, sat, sun).
user (facultatif) : nom d'utilisateur avec lequel exécuter la tâche.
tâche : commande à exécuter.
> log (facultatif) : redirection de la sortie vers un fichier de log. Si un fichier de log n'est pas spécifié, un mail sera envoyé à l'utilisateur local.


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
