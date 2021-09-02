Syntaxe : 

    mm hh jj MMM JJJ [user] tâche > log
    
 lister : crontab -l
 editer : crontab -e
 supprimer tous : crontab -r



Tous les jour a 22h :

    00 22 * * * /root/scripts/sauvegarde.sh >> sauvegarde.log

toute les 6 heures : 

    00 */6 * * * /root/scripts/synchronisation-ftp.sh
    
    
toute les heures : 

    00 */1 * * * /usr/sbin/ntpdate fr.pool.ntp.org
    
toute les minute seulement le lundi :

    * * * * 1 /root/script/commandes-du-lundi.sh
    
    
22 decembre a 00h15 ( une fois par an ) :

    15 00 25 12 * echo "Le père Noël est passé !"
    

