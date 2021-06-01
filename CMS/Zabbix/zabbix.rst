Zabbix
=======


Zabbix est un CMS qui permet de visualiser des statistiques en temps réel sur plusieurs serveurs ou autres installations.


Lien de l'intégration et téléchargement zabbix 
::

  https://www.zabbix.com/fr/download?zabbix=5.0&os_distribution=debian&os_version=10_buster&db=mysql&ws=nginx
  
Des agents zabbix doivent êtres placé sur les serveurs d'écoute


Créer un fichier de config sur un agent : 
::

   mkdir zabbix_agentd.conf.d
   
start, restart, reload or stop zabbix-agent :
::

  systemctl status zabbix-agent

::

  systemctl zabbix_agentd.d start


- Les configuration UserParameter vont dans zabbix-agentd.conf
