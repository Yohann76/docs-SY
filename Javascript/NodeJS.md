## NodeJS Utilisation basique

[Cours JS/Node developpez.com](https://nodejs.developpez.com/tutoriels/javascript/redecouvrir-javascript-avec-nodejs/)


    node --version

# premier programme à executer

    var http = require('http');
    http.createServer(function (req, res) {
        res.writeHead(200, {'Content-Type': 'text/plain'});
        res.end('Hello World\n');
    }).listen(1337, '127.0.0.1');

    console.log('Server running at http://127.0.0.1:1337/');

available in

    $ node hello.js

Server running at http://127.0.0.1:1337/
