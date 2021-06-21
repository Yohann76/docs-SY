## Sqlite


[SqLite Docs](https://www.sqlite.org/docs.html)

SQLite est un utilitaire de base de donnée qui ne necessite pas de base de donnée sur serveur. Nous utilisons notre propre stockage qui est un fichier
SQLite.

Avantage:
- Sauvegarde de BDD uniquement en sauvegardant un fichier
- utilisable localement
- utile pour les fonctionnalité hors connexion ( BDD en local )

inconveniant:
- plus lent si la taille de la BDD est importante
- plusieurs utilisateurs ne peuvent pas modifier une base simulanément
- extension parfois non activé sur les hebergement mutualisé

utilisation:
-----------

dans le php.ini
::
   extension=php_pdo_sqlite.dll
   extension=php_sqlite3.dll

verifier que SQLlite fonctionne ( faire fonctionner ce script )
::
   <?php
   $dbname='base';
   if(!class_exists('SQLite3'))
      die("SQLite 3 NOT supported.");

   $base=new SQLite3($dbname, 0666);
   echo "SQLite 3 supported.";
   ?>


creation de base de donnée et table
::
   $dbname='base';
   $mytable ="tablename";

   if(!class_exists('SQLite3'))
   die("SQLite 3 NOT supported.");

   $base=new SQLite3($dbname, 0666);

   $query = "CREATE TABLE $mytable(
               ID bigint(20) NOT NULL PRIMARY KEY,
               post_author bigint(20) NOT NULL,            
               post_date datetime,
               post_content longtext,
               post_title text,
               guid VARCHAR(255)            
               )";

   $results = $base->exec($query);


supprimer une table
::
   $query = "DROP TABLE $mytable";
   $results = $base->exec($query);

insertion de donnée :
::
   $query = "INSERT INTO $mytable(ID, post_title, post_content, post_author, post_date, guid)
                  VALUES ('$number', '$title', '$content', '$author', '$date', '$url')";
   $results = $base->exec($query);


Le fichier SQLlite:
-----------


Utilisation avec symfony:
-----------
