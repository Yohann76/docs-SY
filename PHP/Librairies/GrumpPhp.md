Instalation
===================
`Github docs`_
composer require --dev phpro/grumphp-shim

Config ( dossier grumphp.yml ) 
===================
::

    parameters:
        tasks:
            composer:
                file: ./composer.json
                no_check_all: false
                no_check_lock: false
                no_check_publish: false
                no_local_repository: false
                with_dependencies: false
                strict: false
            phpcsfixer2:
                allow_risky: ~
                cache_file: ~
                config: '.php_cs.dist'
                rules:
                    '@Symfony': true
                    line_ending: false
                    array_syntax:
                        syntax: short
                using_cache: ~
                config_contains_finder: true
                verbose: true
                diff: false
                triggered_by: ['php']
            phpmd:
                whitelist_patterns: []
                exclude: []
                ruleset: ['cleancode', 'codesize']
                triggered_by: ['php']
            phpstan:
                autoload_file: ~
                configuration: ~
                level: 0
                force_patterns: []
                ignore_patterns: ['/^tests/']
                triggered_by: ['php']
                memory_limit: "-1"
            phpunitbridge:
                config_file: ~
                testsuite: ~
                group: []
                always_execute: false
            phpversion:
                project: '7.3'
            securitychecker:
                lockfile: ./composer.lock
                format: ~
                end_point: ~
                timeout: ~
                run_always: false
            twigcs:
                path: './templates'
                severity: 'warning'
                ruleset: 'FriendsOfTwig\Twigcs\Ruleset\Official'
                triggered_by: ['twig']


Grump php est un "composant" qui permet de verifier a chaque commit si le code est valide, cela permet de vérifier l'ensemble du projet selon certain critére. 

.. _`Github docs`: https://github.com/phpro/grumphp