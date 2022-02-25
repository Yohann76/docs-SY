## CSS

## Variable


    :root {
      --main-bg-color: brown;
    }

    .un {
      background-color: var(--main-bg-color);
    }


## Propriété

    background-color : green ; // background color green
    margin : 0px ; // Marge extérieur
    padding : 0% ; // marge intérieur
    margin-top : 2px ; // marge extérieur haut
    margin-bottom : 2px ; // marge extérieur bas
    margin-left : 2% ; // marge extérieur gauche
    margin-right : 20% ; // marge extérieur droite
    border-radius : 15px ; //  bord arrondi, utilisé pour faire un rond

## Les bordures

    border: 3px blue dashed; // bordur 3px bleu, style de bordure : none - solid - dotted - dashed - double - groove - ridge - inset - outset
    border: 3px blue dashed; // bordur seulement en bas
    border-radius: 10px 5px 10px 5px; // bordur avec 10px en haut a gauche, 5px en haut a droite, 10px en bas a droite et 5px en bas a gauche

## Les ombres

    box-shadow: 6px 6px 6px black; // bordure : 1 bordur normal, 2 l'ombre, 3 genre de transparence 4 couleur
    box-shadow: 6px 6px 6px black inset; // méme bordure que la précédente mais avec un effet renfoncer ( ombre intérieur du bloc )
    text-shadow: 2px 2px 4px black; // bordure pour text

## Les dégradé

    background: linear-gradient(blue, white); // dégrader linéaire haut en bas, bleu vers blanc
    background: linear-gradient(to right, blue, white); // dégrader linéaire gauche a droite, bleu droite - blanc gauche
    background: linear-gradient(to bottom right, blue, white); // dégrader diagonal
    background: linear-gradient(70deg, blue, pink); // dégrader avec angle ( 0deg, 90deg,180deg,-90deg )
    background: linear-gradient(red, yellow, blue, orange); // dégrader plusieurs couleurs
    background: linear-gradient(to bottom left, cyan 50%, palegoldenrod 50%); // dégrader avec ligne franche ( deux couleur distinct )
    background: radial-gradient(red, blue); // dégrader radial ( forme de rond )
    background: radial-gradient(red 10px, yellow 30%, #1e90ff 50%); // dégrader rond avec point d'arret
    background: conic-gradient(red, blue); // dégrader conique
    background: conic-gradient(at 0% 30%, red 10%, yellow 30%, #1e90ff 50%); // dégrader conique avec position du centre
    background: conic-gradient(from 45deg, red, orange, yellow, green, blue, purple); // dégrader avec angle différent
    background: linear-gradient(to right, transparent, mistyrose),
      url("https://mdn.mozillademos.org/files/15525/critters.png"); // dégrader avec intégration d'image transparent

## Selection des éléments

    .nomDeLaclasse // selectionne une classe
    #nomDeLaDiv // selectionne une div
    .section // selectionne une section ( ou nav .. )
    nav a // tout élément a descendant d'un élément nav
    nav > a // tout élément a fils direct d'un élément nav

## Styler les liens

    a:link { color: green; }  // par défaut
    a:visited { color: orange; }  // déjà visité
    a:hover { color: black; background-color: red; }  // lors du survol
    a:focus { color: #aaa; text-decoration: line-through; }  // focus clavier
    a:active { color: yellow; }  // lors du clic

Au survol :

    .section :hover

## Curseur

  body{
    cursor: crosshair;
  }
  img{
    cursor: wait;
  }
  a:link{
    cursor:  pointer;
  }

## Forme et 3D

    #triangle-top {
      width  : 0;
      height : 0;
      border-left   : 25px solid transparent;
      border-right  : 25px solid transparent;
      border-bottom : 50px solid green;
    }

    #triangle-right{
      width  : 0;
      height : 0;
      border-top    : 25px solid transparent;
      border-bottom : 25px solid transparent;
      border-left   : 50px solid red;
    }

    .hexagone {
      box-sizing : border-box;
      position : relative;
      width : 121.24356px;
      height : 70px;
      background-color : #008000;
      margin : 35px 0;
    }

    #trapeze{
      border-bottom: 50px solid green;
      border-left  : 25px solid transparent;
      border-right : 25px solid transparent;
      height : 0;
      width  : 50px;
    }

    #losange-90{
      width  : 0;
      height : 0;
      position : relative;
      top : -25px;
      border : 25px solid transparent;
      border-bottom-color : green;
    }


## Variable en css ( fichier bien css )

    :root {
    --main-bg-color: #eaeaea; /* background */ /* rgb(51,118,205) old */
    --second-bg-color: #dcdfe3; /* title card.. */
    --three-bg-color: #4ecdc4; /*  rgb(31, 85, 156)  old */
    --four-bg-color: #f5f5f5; /*  background card*/ /* old transparency */
    --five-bg-color: #2f323a; /*  background left nav */ /* old rgb(28,38,43) */
    }

    background-color: var(--main-bg-color);
    color: var(--three-bg-color);



## Génération de contenu

Les pseudo-éléments ::before, ::after permettent d'insérer du contenu au
début ou à la fin d'un élément, grâce à la propriété content


    #toto::after {
        content: "je suis le dernier";
    }


## Aligner les input d'un form

    label
    {
      width: 40%;
     display: block;
      float: left;
    }

## Style PDF

[CSS propriété](https://developer.mozilla.org/fr/docs/Web/CSS/page-break-after)
