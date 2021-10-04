## CTF methods

Une fois adresse IP de la machine trouvé, lancer un scan avec nmap.

    $   nmap -A IP_ADRESS

Si port 80 ouvert, tester sur naviguateur l'adresse ip. ( voir code source, commentaire...)
  - tester et voir les fichiers avec dirbuster

Si avec dirbuster des fichiers sont trouver, tester sur naviguateur IP_ADRESS/Name_Folder
