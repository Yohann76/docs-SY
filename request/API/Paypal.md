## Paypal


Outils/API pour payer.

[Paypal docs](https://developer.paypal.com/docs/platforms/get-started/)

-------------------

Http client connect paypal, return token


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




Autre methode ( [Paypal checkout](https://www.paypal.com/merchantapps/appcenter/acceptpayments/checkout)  )


    <div id="paypal-button-container"></div>

    <!-- Include the PayPal JavaScript SDK; replace "test" with your own sandbox Business account app client ID -->
     <script src="https://www.paypal.com/sdk/js?client-id=Ad-nmCDN4U0J_u8A2XXUd2JMrEp6BMSRisXjZdzlWyrhGRpqe3YDoQ9sNiLxLIQSOaPRxDl-7DPfQuyg&currency=EUR"></script>


     <!-- jquery -->
     <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js" integrity="sha512-894YE6QWD5I59HgZOGReFYm4dnWc1Qt5NtvYSaNcOP+u1T9qYdvdihz0PPSiiqn/+/3e7Jo4EaG7TubfWGUrMQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>


     <script>
       /*
       var price = $("#getPrice").val();
       console.log(price);
       */
       paypal.Buttons({
         // Sets up the transaction when a payment button is clicked
         createOrder: function(data, actions) {
           return actions.order.create({
             purchase_units: [{
               amount: {
                 value: '{{price}}' // Can reference variables or functions. Example: `value: document.getElementById('...').value` // price is twig var
               }
             }]
           });
         },
         // Finalize the transaction after payer approval
         onApprove: function(data, actions) {
           return actions.order.capture().then(function(orderData) {
             // Successful capture! For dev/demo purposes:
                 // this is a json info ( generate auto paypal )
                 // console.log('Capture result', orderData, JSON.stringify(orderData, null, 2));
                 var transaction = orderData.purchase_units[0].payments.captures[0];
                 // alert('Transaction '+ transaction.status + ': ' + transaction.id + '\n\nSee console for all available details');
                 // ???? me
                 if ( transaction.status == "COMPLETED"  ) {
                     // To do :  set credit
                     document.location.href="{{ path('succes_pay') }}" // redirect on controller function
                     // https://developer.paypal.com/developer/notifications # notification has been effectued

                 }
                 else {
                     document.location.href="{{ path('invalid_pay') }}"
                     // error page ?
                 }
             // When ready to go live, remove the alert and show a success message within this page. For example:
             // var element = document.getElementById('paypal-button-container');
             // element.innerHTML = '';
             // element.innerHTML = '<h3>Thank you for your payment!</h3>';
             // Or go to another URL:  actions.redirect('thank_you.html');
           });
         }
       }).render('#paypal-button-container');
       // account sell : sb-wfh9g2582019@business.example.com  4xxx
       // account buy personal  : sb-lz8752580455@personal.example.com 4xxx*
     </script>
