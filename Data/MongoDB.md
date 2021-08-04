## MongoDB


[MongoDB Docs](https://docs.mongodb.com/)

( L'éxécutable shell est dans le /bin )

1. creer une base de donnée


   use bddTest

2. créer une collection


   db.createCollection(name, options)

3. URI de db


   mongodb://mongodb0.example.com:27017
   mongodb://localhost:27017/shifumi


MongoDB sur un debian INSTALLATION
===================



   echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list



   sudo apt-get update



   sudo apt-get install -y mongodb-org



   sudo systemctl restart mongod

Accès a mongoShell


   Mongo

Autoriser toute les IP


   mongod --bind_ip_all

utils:


   chown mongodb:mongodb /tmp/mongodb-27017.sock
Utilisation
===================

- créer ou utiliser une base


   use mybdd

- se mettre sur un port


   mongo --port 28015

- se connecter depuis une autre machine


   mongo --host mongodb0.example.com:28015

- connexion string


   mongo "mongodb://mongodb0.example.com.local:27017,mongodb1.example.com.local:27017,mongodb2.example.com.local:27017/?replicaSet=replA&ssl=true"


Commande dans shell mongo ( accessible avec 'mongo' )
========================================================

- créer une donnée


   db.myCollection.insertOne( { x: 1 } );

- trouver une donnée


   db.getCollection("stats").find()

- enlever le TTL qui supprime les données régulierement


   db.adminCommand({setParameter:1, ttlMonitorEnabled:false});



Autre
======


- se lier a une ip
   1. mongo --host My-Example-Associated-Hostname
   2. mongo --host 198.51.100.1
   3. mongod --bind_ip localhost,My-Example-Associated-Hostname

::

Restart le service



   sudo systemctl restart mongod

   mongo --bind_ip 127.0.0.1

/etc/mongod.conf configuration
===================



      # mongod.conf

      # for documentation of all options, see:
      #   http://docs.mongodb.org/manual/reference/configuration-options/

      # Where and how to store data.
      storage:
        dbPath: /var/lib/mongodb
        journal:
          enabled: true
      #  engine:
      #  mmapv1:
      #  wiredTiger:

      # where to write logging data.
      systemLog:
        destination: file
        logAppend: true
        path: /var/log/mongodb/mongod.log

      # network interfaces
      net:
        port: 27017
        bindIp: 127.0.0.1, /tmp/mongod.sock, 10.0.86.86


      # how the process runs
      processManagement:
        timeZoneInfo: /usr/share/zoneinfo
        fork: true

      setParameter:
        enableLocalhostAuthBypass: false
      #security:

      #operationProfiling:

      #replication:

      #sharding:

      ## Enterprise-Only Options:

      #auditLog:

      #snmp:

reset : rm -Rf mongodb/*


lancer le serveur avec terminal éteint :


   nohup mongod --bind_ip 0.0.0.0 &

LANCER SERVEUR MONGO RENFORCÉ :


   nohup mongod --bind_ip 0.0.0.0 --setParameter ttlMonitorEnabled=false &

( nohup et & permet d'executer un processus détaché quand la console est fermé )


Sauvegarder une base de donnée Mongo
================================================



   mongodump -d <database_name> -o <directory_backup>



   mongorestore -d <database_name> <directory_backup>

avec la date dans le fichier :



   mongodump --db somedb --collection somecollection --out - | gzip > dump_`date "+%Y-%m-%d"`.gz


Mongo Express ( équivalent phpmyAdmin for mongo )
================================================

[MongoExpress](https://github.com/mongo-express/mongo-express)


   yarn global add mongo-express

- copier default.config.js avec config.js, puis parametrer la connexion dans config.js

Lancer la configuration


   mongo-express

Accès a une base sur une application ( installation non globale )


   mongo-express -u user -p password -d database

Accès a une base distante


   mongo-express -u user -p password -d database -H mongoDBHost -P mongoDBPort

Mode admin


   mongo-express -a -u superuser -p password


exemple fonctionnel (pas toucher) :


   mongo-express -a -U "mongodb://51.83.108.56:27017/wikirun-db"
