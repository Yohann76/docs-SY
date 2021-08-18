Twig
==========

[Twig Doc](https://twig.symfony.com/doc/2.x/index.html)

Commande Lié a twig
--------------------

    $php bin/console make:twig-extension ( créer une extension twig )
    $php bin/console debug:twig ( voir les filtre )


Twig Syntax
-----------

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

Structure If elseif else endif


  	{% if product.stock > 10 %}
  	Available
  	{% elseif product.stock > 0 %}
  	Only {{ product.stock }} left!
  	{% else %}
  	Sold-out!
  	{% endif %}


  	{% if temperature > 18 and temperature < 27 %}
  		<p>It's a nice day for a walk in the park.</p>
  	{% endif %}


  	{% if users %}
      <ul>
          {% for user in users %}
              <li>{{ user.username|e }}</li>
          {% endfor %}
      </ul>
  	{% endif %}

Opérateurs logique
-----------

    {% if nb == 0 %}
    {% if nb => 0 %}
    {% if nb =< 0 %}
    {% if nb == 0 %}
    {% if nb == null %}


Boucle & itération
-----------


    {% for entry in craft.entries.section('news') %}
        {% if loop.first %}
            First!
        {% endif %}
        {{ entry.title }}

    {% endfor %}

itération :

    loop.first
    loop.index
    loop.index0
    loop.revindex0
    loop.last
    loop.length
