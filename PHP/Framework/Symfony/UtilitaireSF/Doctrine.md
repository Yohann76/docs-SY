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

    $ php bin/console doctrine:database:create ( avec port :3306 )

    $ php bin/console make:entity ( Créer une entité -> classe pour une table )
    $ php bin/console make:entity --regenerate ( régénérer getter et setter )

    $ php bin/console make:migration ( Générer la migration )
    $ php bin/console doctrine:migrations:migrate ( run the migration )

    $ php bin/console doctrine:schema:update
    $ php bin/console doctrine:schema:update --force
    $ php bin/console doctrine:schema:update --dump-sql
    $ php bin/console doctrine:database:drop --force ( supprimer la BDD )
    $ php bin/console doctrine:schema:drop --full-database --force ( supprimer les table )

    $ php bin/console doctrine:query:sql "SELECT * FROM article" ( Tester un code SQL)

    $ php bin/console doctrine:fixtures:load ( charger les data des fixtures dans la bdd )

Pour les relation :
-----------------------
::

		$ php bin/console make Entity
		Choisir l'entité a modifier : Category
		champ : user ( pour faire user_id )
		type : relation
		Classe lié : User
		Choisir le type de relation : ManyToOne ....



Relation manyToMany  :
-----------------------
::
 		// form pour add une relation ManyToMany
		if ($form->isSubmitted() && $form->isValid()) {
				 $entityManager = $this->getDoctrine()->getManager();

				 // set organization id
				 $user = $this->getUser();
				 $OrgaFromCurrentUser = $user->getOrganization();
				 // set orga with mission entity
				 $proof->setOrganization($OrgaFromCurrentUser);

				 $entityManager->persist($proof);
				 $entityManager->flush();

				 //dd($form->get('securityMeasure')->getData());

				 // Change status of measure if proof is submit
				 // each measure send in form ManyToMany
				 // boucle pour faire une action sur chaque entity coché 
				 $countTab = $form->get('securityMeasure')->getData();
				 $i = 0 ;
				 while ($i <= count($countTab)-1) {
						 $data = $form->get('securityMeasure')->getData();
						 $securityMeasure = $data[$i]->setStatus("prouvé");
						 $entityManager->persist($securityMeasure);
						 $entityManager->flush();
						 $i++;
				 }

				 return $this->redirectToRoute('proof_index');
		 }


	$ php bin/console make Entity
	Choisir l'entité a modifier : Category
	champ : user ( pour faire user_id )
	type : relation
	Classe lié : User
	Choisir le type de relation : ManyToMany


pour lié ça à un formulaire :
::

	// update Mission|Collection in activity entity
	->add('mission', EntityType::class, array(
			'class' => Mission::class,
			'multiple' => true,
			'expanded' => true,
			'choice_label' => function(Mission $mission) {
					return sprintf('%s', $mission->getName());
			},
	))

Afficher dans la vue twig :
::

	<!-- list mission of activity RELATION MANY TO MANY -->
	<td>
			{% for t in activity.mission %}
				{{  t.name }}
			{% endfor %}
	</td>
	<!-- end list mission of activity -->


	<!-- Si pas d'envoi en bdd lors d'envoi du form, c'est que la relation est mal faite, dans ce cas,
	inverser dans l'entité, inversedBy=... et mapped=... pour la remettre dans le bon sens -->
