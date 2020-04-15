Twig
==========

`Twig Doc`_

Importer Twig
#############

Les filtres utiles
#############

.. _`Twig Doc`: https://twig.symfony.com/doc/2.x/index.html


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

