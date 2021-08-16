## Nmap - Hacking - Analyse réseau

Commande pour scanner une plage d'adresses :


    $ nmap 192.168.1,.0-255

Commande pour Scanner son réseau local ( et aussi trouver une raspberry ) :


  $ nmap -sP 192.168.0.1/24

Autre
-------------------


    $ nmap 192.168.1.1 // Information sur une IP
    $ nmap -sL 192.168.1.1/24 // Ip sur  réseau avec le nom
    $ nmap -A 192.168.1.45 // Scanner une machine
    $ nmap 192.168.1.1 // scanner un seul host
    $ nmap www.exemple.com // scanner un seul host ou un site
    $ nmap -sS 192.168.1.3 // Scan de port ouvert
    $ nmap -O 192.168.1.3nmap -v -O --osscan-guess 192.168.1.1 // Detecter le systéme d'exploitation d'un host
    $ nmap -p 80 192.168.1.3 // Verifier qu'une machine écoute bien sur un port
