BlackFire
===================

Instalation Windows ?? 


profiler  http://192.168.99.105:8000/ avec blackfire via une ligne de commande sur docker :
docker run -it --rm \
    -e 323c48dc-fe0d-421a-88af-75e9667426f4\
    -e 93d761c659c5ff01f23ed6d99990cfa86b94e6b8c429f3065344a3efecbe5ce5\
    blackfire/blackfire blackfire \
    curl http://192.168.99.105/

créer un alias moins verbeux : 
alias blackfire-curl='docker run -it --rm -e BLACKFIRE_CLIENT_ID -e BLACKFIRE_CLIENT_TOKEN blackfire/blackfire  blackfire curl'  
utiliser cet alias pour profiler :  blackfire-curl http://192.168.99.105:8000