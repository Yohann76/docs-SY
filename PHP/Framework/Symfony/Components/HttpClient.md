## HttpClient

[HttpClient Docs](https://symfony.com/doc/current/components/http_client.html)


Instalation
--------------------------------


    $ composer require symfony/http-client

Exemple
--------------------------------

    use Symfony\Component\HttpClient\HttpClient;

    $client = HttpClient::create();
    $response = $client->request('GET', 'https://api.github.com/repos/symfony/symfony-docs');

    $statusCode = $response->getStatusCode();
    // $statusCode = 200
    $contentType = $response->getHeaders()['content-type'][0];
    // $contentType = 'application/json'
    $content = $response->getContent();
    // $content = '{"id":521583, "name":"symfony-docs", ...}'
    $content = $response->toArray();
    // $content = ['id' => 521583, 'name' => 'symfony-docs', ...]
