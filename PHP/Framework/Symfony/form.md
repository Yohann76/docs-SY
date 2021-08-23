## Formulaire


    $ php bin/console make:form

Controller :

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


  	{{  form_start(form) }}

  	   {{ form_widget(form) }}

  	{{  form_end(form) }}

Type de champ
----------

ChoiceType
----------

    ->add('Roles', ChoiceType::class, [
        'required' => true,
        'multiple' => false,
        'expanded' => false,
        'choices'  => [
            'Administrateur' => 'ROLE_ORGA_ADMIN', # admin orga
            'DPO' => 'ROLE_ORGA_DPO', # DPO orga
            'équipier DPO' => 'ROLE_ORGA_DPO_TEAM', # Team DPO
            'équipier Organisation' => 'ROLE_ORGA_TEAM',  # Team Orga
        ],
    ])

    // form sur entité
    ->add('qualificationSupports', EntityType::class, array(
        'help' => 'Vous pouvez selectionner les types',
        'class' => QualificationSupport::class,
        'multiple' => true,
        'expanded' => true,
        'choice_label' => function(QualificationSupport $qualificationSupport) {
            return sprintf('%s', $qualificationSupport->getName());
        },
    ))
