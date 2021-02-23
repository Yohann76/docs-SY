.. index::
   single: MongoDB; 

MongoDB
===================

`MongoDB Docs`_

.. _`MongoDB Docs`: https://docs.mongodb.com/

( L'éxécutable shell est dans le /bin ) 

1. creer une base de donnée 
   - use bddTest
   
2. créer une collection
   - db.createCollection(name, options)
   
3. URI de db
   - mongodb://mongodb0.example.com:27017  or 
   - mongodb://localhost:27017/shifumi

   
MongoDB sur un debian
===================

- echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list 
- sudo apt-get update
- sudo apt-get install -y mongodb-org
- démarrer un shell mongo : mongo
- sudo systemctl restart mongod

Utilisation
===================

- créer ou utiliser une base : use mybdd
- se mettre sur un port :  mongo --port 28015
- se connecter depuis une autre machine : mongo --host mongodb0.example.com:28015
- connexion string : mongo "mongodb://mongodb0.example.com.local:27017,mongodb1.example.com.local:27017,mongodb2.example.com.local:27017/?replicaSet=replA&ssl=true"
- créer une donnée : db.myCollection.insertOne( { x: 1 } );
- trouver une donnée : db.getCollection("stats").find()

- se lier a une ip 
   1. mongo --host My-Example-Associated-Hostname
   2. mongo --host 198.51.100.1
   3. mongod --bind_ip localhost,My-Example-Associated-Hostname



