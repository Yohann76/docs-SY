## SwiftMailer


    // send mail with data

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
                ]),
                'text/html'
        )
    ;
    $mailer->send($message);
