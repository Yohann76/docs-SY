Paypal
===================

Outils/API pour payer.

`Paypal docs`_

-------------------

Http client connect paypal, return token 
::

   public function connectPaypal() {
        // https://developer.paypal.com/docs/platforms/get-started/#step-1-get-api-credentials
        $response = $this->client->request('POST', 'https://api.sandbox.paypal.com/v1/oauth2/token', [
            'headers' => [
                'Accept' => 'application/json, application/x-www-form-urlencoded',
                'Accept-Language' => 'en_US',
            ],
            'auth_basic' =>  [$this->getPaypalClientIdTest(),$this->getPaypalSecretTest()],
            'body' => ['grant_type' => 'client_credentials']
        ]);
        $content = $response->getContent(); // get Content
        $contentJson = json_decode($content); // get Json

        $tokenPaypalAcces = $contentJson->access_token; // get value "acces_token"
        dump($tokenPaypalAcces);

        // token
        return $tokenPaypalAcces;
    }

    
.. _`Paypal docs`: https://developer.paypal.com/docs/platforms/get-started/