## Symfony

[Symfony docs](https://symfony.com/doc/current/index.html#gsc.tab=0)
[SymfonyConnect](https://connect.symfony.com/)

## Créer un projet


Créer un projet simple ( API ou format court )

    $ composer create-project symfony/skeleton myProject // composer API
    $ composer create-project symfony/website-skeleton my_project_name // composer website
    $ symfony new my_project_name --full // Symfony website ( recommander )
    $ symfony new my_project_name // symfony API

Composer command

    $ composer install ( installer les librairies du composer.json )
    $ composer update ( update les librairies du composer.json )
    $ composer remove symfony/profiler-pack // profiler // Supprimer debug bar

    $ rm -rf vendor/   // pour supprimer toute les dependances /vendor pour réinstaller proprement

Lancer le serveur interne de Symfony

    $ php bin/console server:run
    $ php -S 127.0.0.1:8000 -t public
    $ symfony server:start --no-tls
    $ symfony serve
    $ php bin/console cache:clear

## Composer require utile :

Composer : Les requires indispensable  et commandes composer

  	$ composer unpack ma-librairie //enlever une lib
  	$ composer require server // server
  	$ composer require --dev symfony/profiler-pack // profiler
  	$ composer require security // securité
  	$ composer require logger // log
  	$ composer require twig twig
  	$ composer require form // form
  	$ composer require validation // vérification  pour les form )
  	$ composer require profiler // Profiler
   	$ composer require orm // Bdd
  	$ composer require symfony/maker-bundle --dev // Composant make
  	$ composer require serializer // Serializer pour formater en json ou xml.. (Doc YT )
  	$ composer require doctrine // doctrine
  	$ composer require --dev orm-fixtures  ( Fonction de fixture )
  	$ composer require knplabs/knp-time-bundle pour le filtre ago ( article.publishedAt|ago )
  	$ composer require knplabs/knp-paginator-bundle ( pagination Lien tuto SFCast: )
  	$ composer require apache-pack
  	$ composer require twig/extensions ( filtre twig supplémentaire )
  	$ composer update symfony/maker-bundle
  	$ composer require fzaninotto/faker --dev ( génération de jeux de donnée factice ( en --dev )
  	$ composer require twig/extensions ( Extension Twig )


    $ composer recipes // pour voir la liste des recipe (avec symfony flex)
    // attention si instalation avec force, efface toutes les config de bases.

## Création automatique ( makerBundle )

  	$ php bin/console list make // affiche tout les make
  	$ php bin/console make:controller // créer un controller
  	$ php bin/console generate:bundle
  	$ php bin/console make:command
  	$ php bin/console make:fixtures // ArticleFixtures, CommentFixture..
  	$ php bin/console make:user //créer une entity user avec roles, password, email...
    $ php bin/console make:registration-form // créer un form d'inscription
  	$ php bin/console make:auth // créer un authentificateur
  	$ php bin/console make:voter // créer un voteurs
  	$ php bin/console make:entity // créer/modifier une entité
  	$ php bin/console make:subscriber
  	$ php bin/console make:form // faire un form
  	$ php bin/console make:crud // faire un crud à partir d'une entité
  	$ php bin/console make:functional-test
  	$ php bin/console make:unit-test
    $ php bin/console make:docker:database // ?? add database container in docker-compose.yaml file
    $ php bin/console make:reset-password // create controller, entity and repository for reset password

Commande d’information et Commande divers bin/console

    $ php bin/console
    $ php bin/console debug:autowiring
    $ php bin/console debug:container --parameters ( voir les paramètres ( variable %xx% dans .yaml package )
    $ php bin/console debug:router ( voir toute les routes ).

## Commande symfony de base de donnée

    $ php bin/console doctrine:database:import ./Docs/backup/backup.sql  /// importer une database


(nouvelle commande symfony avec le dernier exécutable ([Symfony executable](https://symfony.com/download))

    $ symfony server:start --no-tls
    $ symfony new --full my_project

Code


Fonction de count pour une entité dans le repository :

    public function countAllUser()
    {
        $qb = $this->createQueryBuilder('e');
        $qb ->select($qb->expr()->count('e'));
        return (int) $qb->getQuery()->getSingleScalarResult();
    }


Service interne les plus utilisé

  	Security $sécurity (   $this->security->getUser()    )
  	LoggerInterface $logger ( $logger->debug(‘xxxxx’)   )


## Bundle utile

créer un bundle (help):


  	$ php bin/console generate:bundle

( convention de nommage Xxx/XxxxBundle ) -> Terminer par Bundle

## Gerer la session [Session docs SF ](https://symfony.com/doc/current/session.html?fbclid=IwAR3vT8p0uYb3eFJ8tdTyG2Io17dsulf9DzeSKZXX6YZ0DosxwB1Q9itdrP4)

La gestion de la session qui est le role de PHP de base peut etre transferer à symfony
(cela evite les problémes d'expiration de session et de duplication de session entre divers site web)

pour que symfony gére la session, il suffit de modifier le config/packages/framework.yaml

    session:
        # ...
        handler_id: 'session.handler.native_file'
        save_path: '%kernel.project_dir%/var/sessions/%kernel.environment%'  

La session sera alors ecrite dans var/session

Le stockage des sessions peut aussi etre utiliser avec un serveur redis (pour un systéme conséquent)

To do : stockage with redis

## Session

Session Users, dispo dans twig avec App.users

transmission de variables :

  	service : Request $request
  	$q = $request->query->get('q');   ( pour une variable “q” )
  	$request->cookies->get('PHPSESSID');
  	// retrieves $_GET and $_POST variables respectively
  	$request->query->get('id');
  	$request->request->get('category', 'default category');

Annotations des routes  :

  	/**
  	* @Route("/admin/comment", name="comment_admin")
  	* @IsGranted("ROLE_ADMIN")
  	*/

Nécessite :
 composer require annotations
 use Sensio\Bundle\FrameworkExtraBundle\Configuration\IsGranted;


Code lié aux requêtes via le repository


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

## Fixtures


Installation / création de la bdd avec les entités :


  	$ php bin/console doctrine:database:create
  	$ php bin/console make:migration ( Générer la migration )
  	$ php bin/console doctrine:migrations:migrate( run the migration ) + y
  	$ php bin/console doctrine:schema:create

Charger les fixtures :


  	$ php bin/console doctrine:fixtures:load
  	$ php bin/console server:run

## Config Symfony :

Les recettes de config sont généré par symfony/flex lors de l'instalation d'un paquet

Ajouter une déconnexion dans security.yaml :

  	logout:
  	path:   logout
  	target: home

Ajouter la fonction remember me


  	remember_me:
  	secret:   '%kernel.secret%'
  	lifetime: 2592000 # 30 days in seconds
  	<input type="checkbox" name="_remember_me"> Remember me  (HTML)


Hierarchy des rôles : ( dans config/packages/security.yaml )


  	role_hierarchy:
  	ROLE_ADMIN: [ROLE_ADMIN_COMMENT, ROLE_ADMIN_ARTICLE, ROLE_ALLOWED_TO_SWITCH]

utiliser un thème de formulaire twig


  	twig:
  	default_path: '%kernel.project_dir%/templates'
  	debug: '%kernel.debug%'
  	strict_variables: '%kernel.debug%'

  	form_themes:
  		- bootstrap_4_layout.html.twig


serveur interne de symfony  : ( source )

  	$ symfony serve ( Lancer le serveur ) ( option -d )
  	$ symfony server:stop ( stopper le serveur )
  	$ symfony local:php:list ( lister les version de php dispo pour le server de sf )

$echo “7.3.5” > .php-version ( utiliser cette version de php pour le symfony serve )
Ou créer une “.php-version” qui contient “7.3.5”

## Code divers


se faire passer pour un utilisateur :
mettre une URL et ajouter ?_switch_user="xxx" ( x est le mail de l’utilisateur )
Nous pouvons désormais naviguer sur le rôle de cet utilisateur
( nécessite ROLE_ALLOWED_TO_SWITCH et switch_user: true ( dans config/packages/security.yaml
 )
et “?_switch_user=_exit” a la fin de l’url pour sortir de ce rôle

Intégrer dans le template une fonction que pour le user/Admin/autre  ( twig )


  	{% if is_granted('ROLE_USER') %} <a href”reserver au user”> {% endif %}

Checker l’utilisateur qui utilise un controller ( dans controller )


  	$logger->debug('Checking account page for '.$this->getUser()->getEmail());

retourner a la page précedente :


  	return $this->redirect($_SERVER['HTTP_REFERER']);

## Création espace de connexion

[Symfony connexion](https://symfony.com/doc/current/the-fast-track/fr/15-security.html#configuring-the-security-authentication)

    $ symfony composer req security
    $ symfony console make:user Admin
    $ symfony console make:migration
    $ symfony console doctrine:migrations:migrate -n
    $ symfony console security:encode-password // généré un password admin

    Authentification

   $ symfony console make:auth

### Security

Utiliser plusieurs providers

# multi provider [SF cos provier](https://symfony.com/doc/current/security/user_providers.html)

    providers:
        # personal provider, request database app.privanciel
        webservice:
            id: App\Security\User\WebserviceUserProvider
            #arguments: ['@doctrine']

        #entity hub
        app_user_provider:
            entity:
                class: App\Entity\User
                property: email

        all_users:
            chain:
                providers: ['webservice', 'app_user_provider']



## Gestion du déploiement :


[Deploiement docs symfony](https://symfony.com/doc/current/deployment.html)
