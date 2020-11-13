Jquery
-------------------

CDN
::

		<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"></script>

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
