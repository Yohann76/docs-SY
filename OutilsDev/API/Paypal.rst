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

    

Js 
::

<script src="https://www.paypal.com/sdk/js?client-id=CLIENT-ID-TOKEN"></script> <!-- Prod Token  -->  
                                                                                 
    <script>
        paypal.Buttons({
            // createOrder est appelé lorsque l'acheteur clique sur l'un des boutons de paiement.
            // Cette fonction doit retourner un numéro de commande ( https://developer.paypal.com/docs/api/orders/v2/#orders )
            // pour rendre le flux de paiement. Dans cet exemple,
            // createOrder appelle votre serveur pour obtenir l'ID de commande.
            createOrder: function (data, actions) {
                // return fetch('/perso/Web-Item-Market/public/createOrder', { // dev
                   return fetch('http://webitemmarket.yohanndurand.fr/createOrder', {
                    method: 'POST'
                }).then(function(res) {
                    if (res.status === 204)
                    {
                        document.location.href="{{ path('errorPayment') }}";
                    }
                    else
                    {
                        return res.json();
                    }
                }).then(function(data) {
                    // console.log(data.id );
                    // console.log(data);
                    return data.id; // return json id
                });
            },
            // Send orderId in methods
            onApprove: function (data, actions) {
                // console.log(data.orderID) ;
                // return fetch('/perso/Web-Item-Market/public/captureOrder/'+data.orderID, { // dev
                return fetch('http://webitemmarket.yohanndurand.fr/captureOrder/'+data.orderID, {
                    method: 'POST'
                }).then(function(res) {
                    console.log(res.status);
                    if (res.status = 200) {
                         document.location.href="{{  path('successPayment') }}";  // OrderID no exist
                    }
                    else {
                        document.location.href="{{ path('errorPayment') }}";
                    }
                });
            }
        }).render('#paypal-button-container');
    </script>
.. _`Paypal docs`: https://developer.paypal.com/docs/platforms/get-started/