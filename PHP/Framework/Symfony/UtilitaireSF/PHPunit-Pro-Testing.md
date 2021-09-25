## Les test avec PHPunit


[PHPunit docs](https://phpunit.readthedocs.io/fr/latest/)

## Commande et installation

prérequis : Installer Xdebug ( sur le wamp )

Composer require :


    composer require phpunit

lancer les test :

    php bin/phpunit

Créer le rapport dans public/data :

    php bin/phpunit --coverage-html public/data

Rapport disponible : http://localhost/oc/SnowTricks/public/data/index.html

Test :

Test Entité (unitaire)  tests/Entity/phoneTest.php

  	<?php

      namespace App\Tests;

      use App\Entity\Phone;
      use PHPUnit\Framework\TestCase;

      class phoneTest extends TestCase
      {
          private $phone;

          public function setUp()
          {
              $this->phone = new Phone();
          }
          public function testPhoneName()
          {
              $this->phone->setName('Iphone');
              $this->assertEquals('Iphone', $this->phone->getName());
          }
      }


Test controller (fonctionnelle) tests/Controller/homecontrollerTest


    <?php

    namespace App\Tests\Controller;

    use Symfony\Bundle\FrameworkBundle\Test\WebTestCase;

    class homeControllerTest extends webTestCase
    {
        public function testIndex()
        {
            $client = static::createClient();
            $client->request('GET', '/');
            $this->assertEquals(200, $client->getResponse()->getStatusCode());
        }
    }


Test Formulaire (fonctionnelle)


    public function testFormCreateActionUser(){
        $client = $this->login('Yohann','dev') ;
        $crawler = $client->request('GET', '/users/create');

        $form = $crawler->selectButton('Ajouter')->form();
        $form['user[username]'] = 'UserTest';
        $form['user[password][first]'] = 'dev';
        $form['user[password][second]'] = 'dev';
        $form['user[email]'] = 'UserTest@gmail.com';
        $form['user[Roles]'] = 'ROLE_USER';

        $crawler = $client->submit($form);

        $client->followRedirect(); // Suivre la redirection si il y a

        $this->assertEquals(200, $client->getResponse()->getStatusCode());
    }

Les éléments sont à trouvé en html comme "user[email]" ou le bouton "ajouter"
Sinon, faire un ->getName sur l'objet $form
