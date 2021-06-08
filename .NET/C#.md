C#
===================

Introduction
-------------------
extension : .cs

La compilation en C# ne donne pas un programme binaire, contrairement au C et au C++.
Le code C# est en fait transformé dans un langage intermédiaire (appelé CIL ou MSIL)

Possibilité : Site internet, intranet, application windows, jeux de carte...

langage de programmation phare de Microsoft
Principalement utilisé avec .NET

Il est possible de créer des programmes (.exe) qui pourront directement être exécuté par le CLR,
mais il est également possible de créer des bibliothèques sous la forme d'un fichier possédant l'extension « .dll ».

Les fichiers .exe sont des assemblys de processus
Les fichiers .dll sont des assemblys de bibliothèques

le fichier .exe servira à lancer une application et qu'une dll pourra être partagée
 entre plusieurs applications .exe afin de réutiliser du code déjà écrit.



Variable
-------------------
::

  int age = 30;
  string prenom = "nicolas";
  decimal soldeCompteBancaire = 100;
  bool estVrai = true;

  Console.WriteLine(age); // affiche 30


Type var framework .NET :
::

  byte : Entier de 0 à 255
  short : Entier de -32768 à 32767
  int : Entier de -2147483648 à 2147483647
  long : Entier de -9223372036854775808 à 9223372036854775807
  float : Nombre simple précision de -3,402823e38 à 3,402823e38
  double : Nombre double précision de -1,79769313486232e308 à 1,79769313486232e308
  decimal : Nombre décimal convenant particulièrement aux calculs financiers (en raison de ses nombres significatifs après la virgule)
  char : Représente un caractère
  string : Une chaine de caractère
  bool : Une valeur booléenne (vrai ou faux)


Opérateurs de comparaison
::

  == : égalité
  !=  : Différence
  > :Supérieur à
  < : Inférieur à
  ! : Négation
  && : ET logique
  || : OU logique

-------------------


Conditions
-------------------
::

    if (civilite == "Mme")
        Console.WriteLine("Vous êtes une femme");
    else if (civilite == "Mlle")
        Console.WriteLine("Vous êtes une femme non mariée");
    else if (civilite == "M.")
        Console.WriteLine("Vous êtes un homme");
    else
        Console.WriteLine("Je n'ai pas pu déterminer votre civilité");


Divers
-------------------
::

    Console.WriteLine("Hello World !!");
