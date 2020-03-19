##################
Commande 
##################

Commande de base 
================

Avec composer : 
****************

Créer un projet simple ( API ou format court )
.. code-block:: terminal

    $ composer create-project symfony/skeleton myProject


Créer un projet complexe ( Application, librairie deja présente )
.. code-block:: terminal

    $ composer create-project symfony/website-skeleton my_project_name


Avec Symfony : 
.. code-block:: terminal

    $symfony new my_project_name --full ( Version Website ) 
    $symfony new my_project_name ( créer un projet avec API ou simple ) 


composer install ( installer les librairies du composer.json ) 
composer update ( update les librairies du composer.json ) 

Lancer le serveur interne de Symfony
.. code-block:: terminal
    $ php bin/console server:run   
    $ php -S 127.0.0.1:8000 -t public
    $ symfony server:start --no-tls
    $ symfony serve 
    $ php bin/console cache:clear 

Composer : Les requires indispensable  et commandes composer 

enlever une lib : 
::
	composer unpack ma-librairie

server : 
::

	composer require server 

securité  :
::

	composer require --dev symfony/profiler-pack
	composer require security

log :
::

	composer require logger

twig :
::

	composer require twig 

form :
:: 

	composer require form

validator :
::

	composer require validation ( vérification  pour les form )

Profiler :
::

	composer require profiler

Bdd  :
::

 	composer require orm 

Composant make:
::

	composer require symfony/maker-bundle --dev

Serializer pour formater en json ou xml.. (Doc YT ) :
::
 
	composer require serializer


	
*doctrine : composer require doctrine
*composer require --dev orm-fixtures  ( Fonction de fixture ) 
*composer require knplabs/knp-time-bundle pour le filtre ago ( article.publishedAt|ago )
*composer require knplabs/knp-paginator-bundle ( pagination Lien tuto SFCast: ) 
*composer require apache-pack
*composer require twig/extensions ( filtre twig supplémentaire ) 
*composer update symfony/maker-bundle
*composer require fzaninotto/faker --dev ( génération de jeux de donnée factice ( en --dev ) 
*composer require twig/extensions ( Extension Twig ) 

Création automatique ( makerBundle )
------------------------------------

*php bin/console make:controller
*php bin/console generate:bundle
*php bin/console make:command
*php bin/console make:fixtures ( ArticleFixtures, CommentFixture.. )
*php bin/console make:user
*php bin/console make:auth ( créer un authentificateur ) 
*php bin/console make:voter ( créer un voteurs )
*php bin/console make:entity


Commande lié a doctrine 
-----------------------

.. code-block:: terminal

    $php bin/console doctrine:database:create ( avec port :3306 )

    $php bin/console make:entity ( Créer une entité -> classe pour une table ) 
    $php bin/console make:entity --regenerate ( régénérer getter et setter )

    $php bin/console make:migration ( Générer la migration ) 
    $php bin/console doctrine:migrations:migrate ( run the migration )

    $php bin/console doctrine:schema:update
    $php bin/console doctrine:schema:update --force
    $php bin/console doctrine:schema:update --dump-sql
    $php bin/console doctrine:database:drop --force ( supprimer la BDD ) 
    $php bin/console doctrine:schema:drop --full-database --force ( supprimer les table ) 

    $php bin/console doctrine:query:sql "SELECT * FROM article" ( Tester un code SQL) 

    $php bin/console doctrine:fixtures:load ( charger les data des fixtures dans la bdd ) 

Pour les relation : 
Faire un make Entity, entrer l’entité A, ensuite mettre “relation” et “B” par exemple 

Commande Lié a twig 
--------------------
.. code-block:: terminal
    $php bin/console make:twig-extension ( créer une extension twig )
    $php bin/console debug:twig ( voir les filtre ) 
    
Commande d’information et Commande divers 

.. code-block:: terminal
    $php bin/console
    $php bin/console debug:autowiring
    $php bin/console debug:container --parameters ( voir les paramètres ( variable %xx% dans .yaml package ) 
    $php bin/console debug:router ( voir toute les routes ).

Nouvelles commandes 
( nouvelle commande symfony avec le dernier exécutable ( https://symfony.com/download ) ) 

.. code-block:: terminal

    $ symfony server:start --no-tls
    $ symfony new --full my_project

Code
#######

Cette partie présente des démonstrations codé

Service interne les plus utilisé 
--------------------------------
::

	Security $sécurity (   $this->security->getUser()    )
	LoggerInterface $logger ( $logger->debug(‘xxxxx’)   )

Bundle utile 
------------ 

créer un bundle (help):
::

	php bin/console generate:bundle 

( convention de nommage Xxx/XxxxBundle ) -> Terminer par Bundle

Session 
-------

Session Users, dispo dans twig avec App.users

transmission de variables :
::

	service : Request $request
	$q = $request->query->get('q');   ( pour une variable “q” )
	$request->cookies->get('PHPSESSID');
	// retrieves $_GET and $_POST variables respectively
	$request->query->get('id');
	$request->request->get('category', 'default category');

Twig Syntax 
-----------
::

	{% block title %}Hello {{ controller_name }}!{% endblock %}
	{{ article.author }}
	{{ path('article_show', {'slug': comment.article.slug}) }}
	{{ comment.createdAt|ago }}  ( filtre ) 
	{{ app.request.query.get('q') }}
	{{ app.user.firstName }}

situer une route dans un contrôleur ( si … = dashboard .. )  
*{{ dump(app.request.get('_route')) }}

*{% form_theme registrationForm _self %}
*{{ form_row(articleForm.specificLocationName) }}


*{% if is_granted('ROLE_USER') %} <a href”reserver au user”> {% endif %}


Annotations des entités  : 
---------------------------

::
	/**
	* @ORM\OneToMany(targetEntity="App\Entity\Comment", mappedBy="article")
	* @ORM\OrderBy({"createdAt" = "DESC"})
	*/


	/**
	* @ORM\ManyToOne(targetEntity="App\Entity\Article", inversedBy="comments")
	* @ORM\JoinColumn(nullable=false)
	*/

	/*Modéliser la relation des deux coté*/
	/**
	* @ORM\ManyToMany(targetEntity="App\Entity\Tag", inversedBy="articles")
	*/


	* @ORM\OrderBy({"createdAt" = "DESC"})
	* @ORM\OneToMany(targetEntity="App\Entity\Comment", mappedBy="article")

Annotations des routes  : 
::
	/**
	* @Route("/admin/comment", name="comment_admin")
	* @IsGranted("ROLE_ADMIN")
	*/   
( nécessite : composer require annotations ) 




Code lié aux requêtes 
---------------------
::
	public function findByExampleField($value)
	{
	   return $this->createQueryBuilder('c')
	       ->andWhere('c.exampleField = :val')
	       ->setParameter('val', $value)
	       ->orderBy('c.id', 'ASC')
	       ->innerJoin('c.article', 'a');
	       ->setMaxResults(10)
	       ->getQuery()
	       ->getResult()
	   ;
	}


Exploitation des API
---------------------

Se référer à la docs spécial API

Formulaire 
----------

Générer du côté vue : 
::
	{{  form_start(form) }}

	   {{ form_widget(form) }}

	{{  form_end(form) }}

Controller : 
::
	$form = $this->createForm(TricksType::class, $tricks);
	//  $form->handleRequest($request);

	return $this->render('admin/tricksEdit.html.twig', [
	   'tricks' => $tricks,
	   'form' => $form->createView()
	]);

	Pour créer un form : php bin/console make:form
	-> nom de la class “ ex TricksType”
	->nom de l'entrée à gérer 


Fixture
--------

Besoin de : 
Exportation en production  

Installation / création de la bdd avec les entités :
::

	-php bin/console doctrine:database:create
	-php bin/console make:migration ( Générer la migration ) 
	-php bin/console doctrine:migrations:migrate( run the migration ) + y  
	-php bin/console doctrine:schema:create

Charger les fixtures :
::

	-php bin/console doctrine:fixtures:load
	-php bin/console server:run


Code divers
------------
se faire passer pour un utilisateur : 
mettre une URL et ajouter ?_switch_user="xxx" ( x est le mail de l’utilisateur ) 
Nous pouvons désormais naviguer sur le rôle de cet utilisateur
( nécessite ROLE_ALLOWED_TO_SWITCH et switch_user: true ( dans config/packages/security.yaml 
 ) 
et “?_switch_user=_exit” a la fin de l’url pour sortir de ce rôle 

Intégrer dans le template une fonction que pour le user/Admin/autre  ( twig ) 
::

	{% if is_granted('ROLE_USER') %} <a href”reserver au user”> {% endif %}

Checker l’utilisateur qui utilise un controller ( dans controller ) 
::

	$logger->debug('Checking account page for '.$this->getUser()->getEmail());

retourner a la page précedente : 
::

	return $this->redirect($_SERVER['HTTP_REFERER']);


Configuration : 
---------------
Ajouter une déconnexion dans security.yaml
::

	logout:
	path:   logout
	target: home

Ajouter la fonction remember me 
::

	remember_me:
	secret:   '%kernel.secret%'
	lifetime: 2592000 # 30 days in seconds
	<input type="checkbox" name="_remember_me"> Remember me  (HTML)


Hierarchy des rôles : ( dans config/packages/security.yaml )
::

	role_hierarchy:
	ROLE_ADMIN: [ROLE_ADMIN_COMMENT, ROLE_ADMIN_ARTICLE, ROLE_ALLOWED_TO_SWITCH]

utiliser un thème de formulaire twig 
::

	twig:
	default_path: '%kernel.project_dir%/templates'
	debug: '%kernel.debug%'
	strict_variables: '%kernel.debug%'

	form_themes:
		- bootstrap_4_layout.html.twig


serveur interne de symfony  : ( source ) 
::

	$symfony serve ( Lancer le serveur ) ( option -d ) 
	$symfony server:stop ( stopper le serveur )
	$symfony local:php:list ( lister les version de php dispo pour le server de sf ) 

$echo “7.3.5” > .php-version ( utiliser cette version de php pour le symfony serve ) 
Ou créer une “.php-version” qui contient “7.3.5” 


Migration d'application : 
---------------

Voir sur github symfony/symfony -> changelog.org.. version qu'on veux upgrade ( 3.4 ) 

a partir de 3.1 : 

Clone -> composer install 

composer update pour mettre a jour sur 3.1 ? 

3.1 a 3.3 : 


////////////////////////////////////////////////////////////////////////
3.1 -> 3.3 -> symfony flex -> 3.4 -> 4.4 
	plusieurs resource : SfCast update to Sf 4 flex .. ( Dans Sf 3 ) 
	Github.com/symfony/symfony -> changelang upgrade ( 3.4 ) 
	Regler les dépréciation au fur et a mesurs 
	( version de php 7.+ no problem )

	BDD
	-> migration : R a faire ( sauf modif de base ) 

////////////////////////////////////////////////////////////////////////












