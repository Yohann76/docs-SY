Formulaire
----------
::

  $ php bin/console make:form

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
