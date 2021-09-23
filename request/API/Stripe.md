## Stripe


Outils/API pour payer.

[Stripe docs](https://stripe.com/docs)


## Session Stripe

    $session = \Stripe\Checkout\Session::create([
        'payment_method_types' => ['card'],
        'line_items' => [[
            'name' => $product->getName(),
            'description' => $product->getDescription(),
            //'images' => ['./' . $product->getImg1()],
            'amount' => $price,
            'currency' => 'eur',
            'quantity' => 1,
        ]],
        'success_url' => 'https://sucessURL/'. $order->getId(),
        'cancel_url' => 'https://CancelURL',
        ]);
