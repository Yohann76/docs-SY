## AlpineJS


::
    
    <h1 x-data="{ message: 'I ❤️ Alpine' }" x-text="message"></h1> <!-- Declarer une variable et l'afficher -->
    
    <div x-data="{ count: 0 }"> <!-- declarer une variable -->
	<button x-on:click="count++">Increment</button> <!-- dRéagir au click -->

	<span x-text="count"></span> <!-- afficher -->
    </div>
