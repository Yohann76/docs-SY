# Sentry

Sentry est une gestionnaire d'erreur qui permet de repérer toutes les erreurs en production
[Sentry Docs for Symfony](https://docs.sentry.io/platforms/php/guides/symfony/)


    composer require sentry/sentry-symfony

    Dans config/sensio_framework_extra

        sensio_framework_extra:
           psr_message:
              enabled: false


    config/packages/sentry.yaml

    sentry:
        dsn: "%env(SENTRY_DSN)%"


        ###> sentry/sentry-symfony ###
        SENTRY_DSN="https://a0f5ebc072a24236ac6a0d05a10b5ac6@o1113647.ingest.sentry.io/6144341"
        ###< sentry/sentry-symfony ###
