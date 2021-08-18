Gitlab CI Example ( Yohann maintener )
===================

Config GitlabCI pour push un projet SF avec Ansible et vérification ( sécurité, phpcs , phpstan , twig-lint)
-------------------


    image: jakzal/phpqa:php7.4

    before_script:
        - composer install

    cache:
        paths:
            - vendor/

    stages:
        - SecurityChecker
        - CodingStandards
        - UnitTests

    security-checker:
        stage: SecurityChecker
        script:
            - local-php-security-checker  --path=./composer.lock
        allow_failure: false

    phpcs:
        stage: CodingStandards
        script:
            - phpcs -v --standard=PSR12 --ignore=./src/Kernel.php ./src
        allow_failure: true

    phpstan:
        stage: CodingStandards
        script:
            - phpstan analyse ./src
        allow_failure: true

    twig-lint:
        stage: CodingStandards
        script:
            - twig-lint lint ./templates
        allow_failure: true

    phpunit:
        image: php:7.4-apache
        stage: UnitTests
        services:
            - name: mysql:5.7
              alias: mysql
        variables:
          MYSQL_ROOT_PASSWORD: pass_test
          MYSQL_DATABASE: myapptest
          MYSQL_USER: myapptest
          MYSQL_PASSWORD: myapptest
          DATABASE_URL: 'mysql://myapptest:myapptest@mysql:3306/myapptest'
        before_script:
            - apt-get update && apt-get install -y git libzip-dev
            - curl -sSk https://getcomposer.org/installer | php -- --disable-tls && mv composer.phar /usr/local/bin/composer
            - docker-php-ext-install mysqli pdo pdo_mysql zip
            - php bin/console doctrine:database:drop --force --env=test
            - php bin/console doctrine:database:create --env=test
            #- php bin/console doctrine:migration:migrate --env=test --no-interaction
            - php bin/console doctrine:schema:update --force --env=test
            - php bin/console doctrine:fixture:load --no-interaction --env=test
        script:
            - php bin/phpunit
        allow_failure: false
