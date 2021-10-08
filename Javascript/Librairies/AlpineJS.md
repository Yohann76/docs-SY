## AlpineJS

[Alpine JS Github](https://github.com/alpinejs/alpine)
[Alpine JS Docs](https://alpinejs.dev/)
[Alpine JS Docs (instalation..module..)](https://alpinejs.dev/essentials/installation)

## CDN

    <script defer src="https://unpkg.com/alpinejs@3.x.x/dist/cdn.min.js"></script>

## Exemple

    <h1 x-data="{ message: 'I ❤️ Alpine' }" x-text="message"></h1> <!-- Declarer une variable et l'afficher -->

    <div x-data="{ count: 0 }"> <!-- declarer une variable -->
	   <button x-on:click="count++">Increment</button> <!-- dRéagir au click -->
	   <span x-text="count"></span> <!-- afficher -->
    </div>


## autre lien utile
