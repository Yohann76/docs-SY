Jquery
-------------------

CDN
::

		<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.5.1/jquery.js" integrity="sha512-WNLxfP/8cVYL9sj8Jnp6et0BkubLP31jhTG9vhL/F5uEZmg5wEzKoXp1kJslzPQWwPT1eyMiSxlKCgzHLOTOTQ==" crossorigin="anonymous"></script>

Sélection du DOM
::

	$(document).ready(function() {
    $('.class').on('click', function() {
            console.log('todo delete!');
        });
    }


compter le nombre de div
-------------------
::

		Var nbDiapos = $('div.diapo').length;


Evenement Jquery
-------------------
::

		.on('click', function() { … }
		.on('scroll', function() { … }
		.on('hover', function() { … }
		.on('mouseover', function() { … }
		.on('mouseenter', function() { … }
		.on('mouse leave', function() { … }
		.on('keydown', function() { … }
		.on('keyup', function() { … }
		.on('keypress', function() { … }
		.on('focus', function() { … }
		.on('blur', function() { … }
		.on('resize', function() { … }
