## Swift Mailer

## Code exemple Controller Symfony

    $message = (new \Swift_Message('Invitation Blitz'))
                    ->setFrom('yohanndurand76@gmail.com')
                    ->setTo($form->get('email')->getData()) // get email from form
                    ->setBody(
                        $this->renderView(
                            'Emails/sendInviteOrga.html.twig',
                            [
                                'mail' => $invited,
                                'NameOrga' => $OrgaFromCurrentUser->getName(),
                                'password' => $form->get('password')->getData(),
                                'id' => $id, # for edit in email
                            ]),
                            'text/html'
                    )
    ;
    $mailer->send($message);



[SwiftMailer docs](https://swiftmailer.symfony.com/docs/introduction.html)
