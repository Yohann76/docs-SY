Les bases du PHP
===================


Fonction utile dans PHP 
############ 

Trouver la longueur d'une chaine de caractere : 
:
    strlen()

modifie une chaine de caractere avec un parametre d'entrée et de sortie :
::
    substr("abcdef", 0, -1);  // retourne "abcde"

Cherche la position d'un premier motif dans une chaine :
::
    strpos($mystring, $findme);  // retourne un int : la premier occurence

Fonctions de chiffrements : 
- base64_encode($content) && base64_decode($content);
- encrypt($data) && decrypt($data)


Generer un serveur PHP
############


Expressions réguliere  
############


Une regex sert a trouver un motif dans une chaine de caractere: 

Cette fonction preg_match_all renvoie tout les chaine de caractere qui commence par 'https://'
::
    preg_match_all("#(https?://)([\w\d.&:\#@%/;$~_?\+-=]*)#",$fileContent, $out);

Il existe aussi la fonction preg_match qui envoie true ou false selon si un motif est trouvé ou non

Regex utile: 
::
    #(https?://)([\w\d.&:\#@%/;$~_?\+-=]*)#  // trouve une chaine https://

