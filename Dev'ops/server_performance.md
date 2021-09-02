Regarder l'utilisation de la mémoire RAM en temps réel : 

    watch -n 1 free -m
    
Vider le cache de la RAM :

    free -h && sudo sysctl vm.drop_caches=3 && free -h
    
Regarder les processus:

    top
    
Utilitaire pour la gestion de la RAM ( Zram ) 

[zRam](https://www.linuxtricks.fr/wiki/zram-compresser-la-ram-au-lieu-de-swapper-sur-linux)
    
Utilitaire pour la gestion du swap : Zswap 
    

