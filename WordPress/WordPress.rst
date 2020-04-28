WordPress
===================



Créer un thème enfant 
================

`Tuto WP`_

Dans le dossier wp-content/themes. on cré un dossier : 
/nomdevotrethemeenfant

ensuite on crée deux fichier:
-functions.php
-style.css 


dans le function.php on y met : 

------------------------------------------
<?php
/**
** activation theme
**/
add_action( 'wp_enqueue_scripts', 'theme_enqueue_styles' );
function theme_enqueue_styles() {
 wp_enqueue_style( 'parent-style', get_template_directory_uri() . '/style.css' );

}
------------------------------------------

et dans le style.css on y met : 

------------------------------------------
/*
Theme Name: Theme enfant
Description: Theme enfant de Benoit WPServeur
Author: Benoit - WPserveur
Author URI: https://www.wpserveur.net
Template: WPServeur 
Version: 0.1.0
*/
------------------------------------------
INFO :
Theme Name : Le nom que je veux donner a mon thème enfant
Description : La description de mon thème enfant celle qui apparaîtra dans mon gestionnaire de thème WordPress
Author : L’auteur du thème enfant, en l’occurrence c’est vous
Author URI : L’url du site de l’auteur parce qu’un peu de pub ne fait pas de mal
Template : Le nom du thème parent en l’occurrence le nom du répertoire tel qu’il est écrit sur le FTP
Version : La version de votre thème enfant à titre indicatif


RAPELL :
Ne jamais mettre d’espace avant les deux points. Theme Name: fonctionnera 
mais Theme Name : ne fonctionnera pas
Pour l’attribut Template : Si votre thème dans l’admin se nomme par exemple 
“wpserveur” mais que le nom affiché dans le répertoire FTP est “WPserveur” alors 
il faudra obligatoirement respecter la casse et écrire WPserveur et non wpserveur


POUR METTRE UNE IMG DE THEME OU MINIATURE 

Afin d’égayer un peu votre gestionnaire de thèmes WordPress,
 vous pourrez aussi mettre un fichier screenshot.jpg (600×450 px conseillé)
 qui affichera la miniature de votre thème enfant dans le gestionnaire de thèmes.
Pour le reste, vous pouvez ne rien mettre, cela fonctionnera quand même !


Traduire son thème 

https://wpformation.com/theme-enfant-wordpress/


Dans le dossier wp-content/themes. on cré un dossier : 
/nomdevotrethemeenfant

ensuite on crée deux fichier:
-functions.php
-style.css 


dans le function.php on y met : 

------------------------------------------
<?php
/**
** activation theme
**/
add_action( 'wp_enqueue_scripts', 'theme_enqueue_styles' );
function theme_enqueue_styles() {
 wp_enqueue_style( 'parent-style', get_template_directory_uri() . '/style.css' );

}
------------------------------------------

et dans le style.css on y met : 

------------------------------------------
/*
Theme Name: Theme enfant
Description: Theme enfant de Benoit WPServeur
Author: Benoit - WPserveur
Author URI: https://www.wpserveur.net
Template: WPServeur 
Version: 0.1.0
*/
------------------------------------------
INFO :
Theme Name : Le nom que je veux donner a mon thème enfant
Description : La description de mon thème enfant celle qui apparaîtra dans mon gestionnaire de thème WordPress
Author : L’auteur du thème enfant, en l’occurrence c’est vous
Author URI : L’url du site de l’auteur parce qu’un peu de pub ne fait pas de mal
Template : Le nom du thème parent en l’occurrence le nom du répertoire tel qu’il est écrit sur le FTP
Version : La version de votre thème enfant à titre indicatif


RAPELL :
Ne jamais mettre d’espace avant les deux points. Theme Name: fonctionnera 
mais Theme Name : ne fonctionnera pas
Pour l’attribut Template : Si votre thème dans l’admin se nomme par exemple 
“wpserveur” mais que le nom affiché dans le répertoire FTP est “WPserveur” alors 
il faudra obligatoirement respecter la casse et écrire WPserveur et non wpserveur


POUR METTRE UNE IMG DE THEME OU MINIATURE 

Afin d’égayer un peu votre gestionnaire de thèmes WordPress,
 vous pourrez aussi mettre un fichier screenshot.jpg (600×450 px conseillé)
 qui affichera la miniature de votre thème enfant dans le gestionnaire de thèmes.
Pour le reste, vous pouvez ne rien mettre, cela fonctionnera quand même !

.. _`Tuto WP`: https://wpformation.com/theme-enfant-wordpress/