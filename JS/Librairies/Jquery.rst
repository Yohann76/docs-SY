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
