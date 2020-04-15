Doctrine sous symfony
===================

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
