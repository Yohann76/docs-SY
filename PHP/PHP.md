## Les bases du PHP


[PHP docs](http://php.net/manual/fr/)

Variable
===================

Concatener une variable dans une chaine de caractére a simple quote
::

    'https://www.google.com/search?q='.$keyword1.'&num=1000'

Les tableau
===================
::
    $theVariable = array("A", "B", "C");

    array(
        key  => value,
        key2 => value2,
        key3 => value3,
        ...
    )

Boucler et pusher dans un tableau ( dans un objet )
-------------------
::

  $ListUser = [];
  foreach ($listUserInOrga as $value) {
      $Userid = $value->getUser() ;
      array_push($ListUser, $Userid);
  }


Function sur tableau
-------------------
::

  unset($arr[5]); // Ceci efface l'élément du tableau
  unset($arr);    // Ceci efface complètement le tableau

Fonction utile dans PHP
===================

Trouver la longueur d'une chaine de caractere :
::
    strlen()

modifie une chaine de caractere avec un parametre d'entrée et de sortie :
::
    substr("abcdef", 0, -1);  // retourne "abcde"

Cherche la position d'un premier motif dans une chaine :
::
    strpos($mystring, $findme);  // retourne un int : la premier occurence

Fonctions de chiffrements :
::

    ( base64 ) base64_encode($content) && base64_decode($content);
    ( encrypt) encrypt($data) && decrypt($data)


savoir la valeur d'une variable :
::

    var_dump($var);

Afficher l'environement php
::

    phpinfo() ;

Generer un serveur PHP
::

    php -S 127.0.0.1:8000 -t public

Executer un fichier php en ligne de commande
::

    php NomDuFichier

[PHP shell-exec](https://www.php.net/manual/fr/function.shell-exec.php)

Trouver le chemin d'un fichier
::

    <?php echo realpath('chemin.php'); ?>

Mettre ce fichier la ou on veux trouver le chemin, et l'executer avec le serveur
cela va nous retransmettre le chemin


remplacer un contenu
::

    $content = str_replace(">", " ",  $content);
    $content = str_replace("<", " ",  $content);

Enlever les espace a un string :
::

    trim($msg);

############


Expressions réguliere
############

[Memento expression reguliere OC](https://openclassrooms.com/fr/courses/918836-concevez-votre-site-web-avec-php-et-mysql/918834-memento-des-expressions-regulieres)

Une regex sert a trouver un motif dans une chaine de caractere:

Cette fonction preg_match_all renvoie tout les chaine de caractere qui commence par 'https://'
::
    preg_match_all("#(https?://)([\w\d.&:\#@%/;$~_?\+-=]*)#",$fileContent, $out);

Il existe aussi la fonction preg_match qui envoie true ou false selon si un motif est trouvé ou non

Regex utile:
::
    #(https?://)([\w\d.&:\#@%/;$~_?\+-=]*)#  // trouve une chaine https://
    preg_match_all("#^\s[a-z0-9._-]+@[a-z0-9._-]{2,}\.[a-z]{2,4}\s$#",$content, $out); // Trouver une adresse mail