Twig
==========

`Twig Doc`_

Commande Lié a twig 
--------------------
.. code-block:: terminal
    $php bin/console make:twig-extension ( créer une extension twig )
    $php bin/console debug:twig ( voir les filtre ) 


Twig Syntax 
-----------
::

	{% block title %}Hello {{ controller_name }}!{% endblock %}
	{{ article.author }}
	{{ path('article_show', {'slug': comment.article.slug}) }}
	{{ app.request.query.get('q') }}
	{{ app.user.firstName }}
	{{ ticketUserClose.createdAt|date('Y-m-d')}} ( filtre de date ) 

situer une route dans un contrôleur ( si … = dashboard .. )  
*{{ dump(app.request.get('_route')) }}

*{% form_theme registrationForm _self %}
*{{ form_row(articleForm.specificLocationName) }}


*{% if is_granted('ROLE_USER') %} <a href”reserver au user”> {% endif %}



.. _`Twig Doc`: https://twig.symfony.com/doc/2.x/index.html

