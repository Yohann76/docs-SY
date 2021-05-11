.. index::
   single: Nmap;

Nmap - Hacking - Analyse réseau
===================

Commande pour scanner une plage d'adresses :
::

    nmap 192.168.1,.0-255

Commande pour Scanner son réseau local ( et aussi trouver une raspberry ) :
::

  nmap -sP 192.168.0.1/24

Autre
-------------------
::

  nmap 192.168.1.1 // Information sur une IP
  nmap -sL 192.168.1.1/24 // Ip sur  réseau avec le nom
  nmap -A 192.168.1.45 // Scanner une machine
