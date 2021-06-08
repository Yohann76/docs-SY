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
  
  /var/ossec/bin/manage_agents -l
  
ajouter un agent:
::

  sudo /var/ossec/bin/manage-agents
  
restart un agent :
::

  /var/ossec/bin/agent_control -R <id_agent>
  
Effectuer un sysCheck :
::

  /var/ossec/bin/agent_control -r -u 001



Generer des clef client.key ( /var/ossec/etc/client.key ) de type suivant, puis inclure le même fichier dans le serveur et le client
::
  <id> <nameAgent> <ip> <key random>
  001 mercure 51.178.95.96 AxIE5vZGUyIDE5Mi4xNjguNDMuMTkzIDJiOGNlNGYyOTU5ZGZkYTNmMDFjNzY5YjUxODRhZmYyNGY1ZjQzYTA3NmFlMWFiNTBkZDU1MmU1MjU3YTRkZmM=
  
  002 callisto 51.83.108.56 b0c5548beda537daddb4da698424d0856c3d4e760eaced803d58c07ad1a95f4c
  
  XXX XXXX XXX.XXX.XXX.XXX 8ec4843da9e61647d1ec3facab542acc26bd0e08ffc010086bb3a6fc22f6f65b
  
  
- Mettre les frequency a 40 
  

  
