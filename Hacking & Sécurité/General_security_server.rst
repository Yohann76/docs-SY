Sécurité générale des serveurs : 

Tips
======

- Utiliser un compte non-root pour installer et gerer le serveur
- UFW pour installer un firewall

HIDS - OSSEC pour la detection d'intrusion 
===========================================

https://all-it-network.com/ossec/

restart, start, stop HIDS OSSEC:
::

  sudo /var/ossec/bin/ossec-control restart
  

Lister les agents actif depuis le serveur :
::

  sudo /var/ossec/bin/agent_control -lc
  
ajouter un agent:
::

  sudo /var/ossec/bin/manage-agents
  
Generer des clef client.key ( /var/ossec/etc/client.key ) de type :
::
  <id> <nameAgent> <ip/24> <key random>
  001 mercure 51.178.95.96/24 AxIE5vZGUyIDE5Mi4xNjguNDMuMTkzIDJiOGNlNGYyOTU5ZGZkYTNmMDFjNzY5YjUxODRhZmYyNGY1ZjQzYTA3NmFlMWFiNTBkZDU1MmU1MjU3YTRkZmM=
  

  
