Regarder l'utilisation de la mémoire RAM en temps réel : 

    watch -n 1 free -m
    
Vider le cache de la RAM :

    free -h && sudo sysctl vm.drop_caches=3 && free -h
    
Regarder les processus:

    top
    

