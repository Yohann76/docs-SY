## SnappyBundle


SnappyBundle est un bundle pour transformer des vue twig en pdf,
çela nécéssite d'installer le binaire de wkhtmltopdf sur windows et sur le serveur

Instalation
-------------------

[Github Knp Snappy Bundle](https://github.com/KnpLabs/KnpSnappyBundle)

  $ composer require knplabs/knp-snappy-bundle


Le binaire
-------------------

windows : [binaire de wkhtmltopdf](https://wkhtmltopdf.org/downloads.html)

Commande sur serveur ( selon machine ) :


    $ wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.trusty_amd64.deb   ( pour ubuntu 16.04 )
    $ sudo dpkg -i wkhtmltox_0.12.5-1.trusty_amd64.deb
    $ sudo apt -f install


  Le binaire doit se trouver sur linux :  WKHTMLTOPDF_PATH=/usr/local/bin/wkhtmltopdf ( d'ou l'info dans le .env )



Le .env
-------------------

    ###> knplabs/knp-snappy-bundle ### # To do : transform env in prod

    # local info
    # WKHTMLTOPDF_PATH="C:\Progra~1\wkhtmltopdf\bin\wkhtmltopdf.exe" # local windows dir # for run this : install wkhtmltopdf binary

    # prod info
    WKHTMLTOPDF_PATH=/usr/local/bin/wkhtmltopdf
    WKHTMLTOIMAGE_PATH=/usr/local/bin/wkhtmltoimage

    ###< knplabs/knp-snappy-bundle ###

Methode pour transformer en pdf
-------------------

    use Knp\Snappy\Pdf;
    use Knp\Bundle\SnappyBundle\Snappy\Response\PdfResponse;

    /**
     * @Route("/pdf/export/registre", name="app_export_registre_pdf", methods={"GET","POST"})
     */
    public function registreExportPDF(\Knp\Snappy\Pdf $snappy,SecurityMeasureRepository $securityMeasure,ProofRepository $proofRepository,ConcernedPersonRepository $concernedPersonRepository,StakeholderRepository $stakeholderRepository,PrivateDataRepository $privateDataRepository,ActivityRepository $activityRepository,MissionRepository $missionRepository, SupportRepository $supportRepository)
    {
        // get orga from current user
        $user = $this->getUser();
        $OrgaFromCurrentUser = $user->getOrganization();

        $html = $this->renderView('Priventiel/PDF/full_registre.html.twig', array(
            'missions' => $missionRepository->findBy(['organization' => $OrgaFromCurrentUser ]),
            'activities' => $activityRepository->findBy(['organization' => $OrgaFromCurrentUser ]), // for copy repository mission in registre
            'supports' => $supportRepository->findBy(['organization' => $OrgaFromCurrentUser ]), // for copy repository mission in registre
            'private_datas' => $privateDataRepository->findBy(['organization' => $OrgaFromCurrentUser ]),
            'supports' => $supportRepository->findBy(['organization' => $OrgaFromCurrentUser ]),
            'concerned_peoples' => $concernedPersonRepository->findBy(['organization' => $OrgaFromCurrentUser ]),
            'stakeholders' => $stakeholderRepository->findBy(['organization' => $OrgaFromCurrentUser ]),
            'proof' => $proofRepository->findBy(['organization' => $OrgaFromCurrentUser ]),
            'securityMeasure' => $securityMeasure->findBy(['organization' => $OrgaFromCurrentUser, 'locked' => null ]),
        ));


        $filename = sprintf('test-%s.pdf', date('Y-m-d'));

        return new PdfResponse(
            //$snappy->setOption('encoding', 'UTF-8'),
            $snappy->getOutputFromHtml($html),
            'full_registre.pdf',
            [
                'Content-Type'        => 'application/pdf',
                'Content-Disposition' => sprintf('attachment; filename="%s"', $filename),
            ]
        );
    }
