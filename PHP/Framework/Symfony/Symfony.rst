Symfony
##################

`Symfony docs`_
`SymfonyConnect`_

Créer un projet
****************

Avec Composer : 
================
Créer un projet simple ( API ou format court )

.. code-block:: terminal

    $ composer create-project symfony/skeleton myProject

Créer un projet complexe ( Application, librairie deja présente )
.. code-block:: terminal

    $ composer create-project symfony/website-skeleton my_project_name

Avec Symfony : 
===============

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

Composer require utile : 
===============

Composer : Les requires indispensable  et commandes composer 
::
	composer unpack ma-librairie //enlever une lib 
	composer require server // server 
	composer require --dev symfony/profiler-pack // profiler
	composer require security // securité  
	composer require logger // log 
	composer require twig twig 
	composer require form // form
	composer require validation // vérification  pour les form )
	composer require profiler // Profiler
 	composer require orm // Bdd 
	composer require symfony/maker-bundle --dev // Composant make
	composer require serializer // Serializer pour formater en json ou xml.. (Doc YT ) 
	composer require doctrine // doctrine
	composer require --dev orm-fixtures  ( Fonction de fixture ) 
	composer require knplabs/knp-time-bundle pour le filtre ago ( article.publishedAt|ago )
	composer require knplabs/knp-paginator-bundle ( pagination Lien tuto SFCast: ) 
	composer require apache-pack
	composer require twig/extensions ( filtre twig supplémentaire ) 
	ycomposer update symfony/maker-bundle
	composer require fzaninotto/faker --dev ( génération de jeux de donnée factice ( en --dev ) 
	composer require twig/extensions ( Extension Twig ) 

Création automatique ( makerBundle )
------------------------------------
::

	php bin/console list make  ( affiche tout les make )
	php bin/console make:controller
	php bin/console generate:bundle
	php bin/console make:command
	php bin/console make:fixtures ( ArticleFixtures, CommentFixture.. )
	php bin/console make:user
	php bin/console make:auth ( créer un authentificateur ) 
	php bin/console make:voter ( créer un voteurs )
	php bin/console make:entity
	php bin/console make:subscriber
	php bin/console make:form
	php bin/console make:crud
	php bin/console make:registration-form
	php bin/console make:functional-test
	php bin/console make:unit-test


Commande d’information et Commande divers 

.. code-block:: terminal
    $php bin/console
    $php bin/console debug:autowiring
    $php bin/console debug:container --parameters ( voir les paramètres ( variable %xx% dans .yaml package ) 
    $php bin/console debug:router ( voir toute les routes ).

Nouvelles commandes 
( nouvelle commande symfony avec le dernier exécutable ( `Symfony executable`_ ) ) 
															
.. code-block:: terminal

    $ symfony server:start --no-tls
    $ symfony new --full my_project

Code
#######

Cette partie présente des démonstrations codé

Faire apelle a une fonction du repository 
--------------------------------
::

    /**
     * @Route("/dashboard/admin", name="app_dashboard_admin")
     */
    public function index(UserRepository $userRepository, OrderRepository $orderRepository, ListMailRepository $listMailRepository)
    {
        $ClientNumber = $userRepository->countAllUser();
        $OrderNumber = $orderRepository->countAllOrder();
        $ListMailNumber = $listMailRepository->countAllListMail();

        return $this->render('dashboard/dashboardAdmin.html.twig', [
            'ClientNumber' => $ClientNumber,
            'OrderNumber' => $OrderNumber,
            'ListMailNumber' => $ListMailNumber
        ]);
    }

Fonction de count pour une entité dans le repository : 
::

    public function countAllUser()
    {
        $qb = $this->createQueryBuilder('e');
        $qb ->select($qb->expr()->count('e'));
        return (int) $qb->getQuery()->getSingleScalarResult();
    }

Dans la vue : 
::

{{ ClientNumber }} {{ OrderNumber }} {{ ListMailNumber }}


Service interne les plus utilisé 
--------------------------------
::

	Security $sécurity (   $this->security->getUser()    )
	LoggerInterface $logger ( $logger->debug(‘xxxxx’)   )


Bundle utile 
-------
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

Annotations des routes  : 
::
	/**
	* @Route("/admin/comment", name="comment_admin")
	* @IsGranted("ROLE_ADMIN")
	*/   
( nécessite : composer require annotations ) 




Code lié aux requêtes via le repository
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

Formulaire 
----------
php bin/console make:form

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

Générer du côté vue : 
::
	{{  form_start(form) }}

	   {{ form_widget(form) }}

	{{  form_end(form) }}


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


Config Symfony : 
---------------
Les recettes de config sont généré par symfony/flex lors de l'instalation d'un paquet

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




Gestion du déploiement : 
---------------

`Deploiement docs symfony`_


.. _`SymfonyConnect`: https://connect.symfony.com/
.. _`Symfony docs`: https://symfony.com/doc/current/index.html#gsc.tab=0
.. _`Deploiement docs symfony`: https://symfony.com/doc/current/deployment.html
.. _`Symfony executable`: https://symfony.com/download 














