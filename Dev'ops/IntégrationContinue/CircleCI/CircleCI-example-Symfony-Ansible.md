## Config circleCI :


    version: 2
    jobs:
    build_and_test:
        docker:
        # Specify the version you desire here
        - image: circleci/php:7.3-node-browsers
        - image: circleci/mysql:5.7-ram

            environment:
            MYSQL_ALLOW_EMPTY_PASSWORD: yes
            MYSQL_ROOT_PASSWORD: root
        steps:
        - checkout

        - run:
            name: Install System Packages
            command: sudo apt update && sudo apt -y install git unzip libxml2 libjpeg-dev libfreetype6-dev libjpeg62-turbo-dev libpng-dev libxslt-dev libzip-dev zlib1g-dev libsqlite3-dev libwebp-dev wget
            # PHP CircleCI 2.0 Configuration File sudo apt install zlib1g-dev libsqlite3-dev
        - run:
            name: Install PHP Extensions
            command: sudo docker-php-ext-install pdo pdo_mysql xsl zip
        #- run:
            #name: Configure gd
            #command: sudo docker-php-ext-configure gd --with-freetype-dir=/usr --with-jpeg-dir=/usr --with-png-dir=/usr
            ##command: sudo docker-php-ext-configure gd --with-freetype --with-jpeg

        #- run:
            #name: Install PHP gd
            #command: sudo -E docker-php-ext-install -j$(nproc) gd

        # Download and cache dependencies
        - restore_cache:
            keys:
                # "composer.lock" can be used if it is committed to the repo
                - portfolio-v1-dependencies-{{ checksum "composer.json" }}
                # fallback to using the latest cache if no exact match is found
                - portfolio-v1-dependencies-

        - run: composer install -n --prefer-dist

        - save_cache:
            key: portfolio-v1-dependencies-{{ checksum "composer.json" }}
            paths:
                - ./vendor

        #- run: chmod -x 777 bin/console
        # run: bin/console cache:clear --env=test
        #- run: bin/console cache:warmup --env=test

        - restore_cache:
            keys:
                - portfolio-node-v1-{{ checksum "package.json" }}
                - portfolio-node-v1-

        - run: yarn install
        - save_cache:
            key: portfolio-node-v1-{{ checksum "package.json" }}
            paths:
                - node_modules

        - run: yarn build

        # Database
        #- run: ./bin/console doctrine:database:create --env=test
        #- run: ./bin/console doctrine:schema:create --env=test
        #- run: ./bin/console doctrine:fixtures:load --env=test --no-interaction


        # Launch tests
        - run: chmod +x bin/phpunit
        - run: bin/phpunit

    configure_and_deploy:
        docker:
        - image: ubuntu:16.04
            environment:
            ANSIBLE_HOST_KEY_CHECKING: no
        steps:
        # Install PIP
        - run:
            name: Install System packages
            command: apt update && apt -y install python3-pip ssh
        # Installation
        - run:
            name: Install Ansible
            command: |
                apt update -y
                apt install -y language-pack-ja-base language-pack-ja
                apt install -y software-properties-common
                apt-add-repository -y ppa:ansible/ansible
                apt update -y
                apt install -y curl python-dev git
                curl "https://bootstrap.pypa.io/get-pip.py" -o "/tmp/get-pip.py"
                python /tmp/get-pip.py
                pip install --upgrade pip && pip install --upgrade setuptools
                pip install ansible

        - run:
            name: Install sshpass
            command: apt-get install sshpass

        # Dependencies
        - checkout

        #- restore_cache:
            #key: portfolio-${CIRCLE_BRANCH}-{{ checksum "./ansible/requirements.yaml" }}-v1

            #- run: ansible-galaxy install -r ansible/requirements.yaml

            #- save_cache:
            #key: portfolio-${CIRCLE_BRANCH}-{{ checksum "./ansible/requirements.yaml" }}-v1

        - run: echo $ANSIBLE_VAULT_PASSWORD > ansible/.vault-pass.txt #$ANSIBLE_VAULT_PASSWORD defined in CircleCi
        - run: ansible-playbook ansible/playbook.yml -i ansible/hosts.ini -e "git_branch=master" --vault-password-file=ansible/.vault-pass.txt
        - run: rm ansible/.vault-pass.txt

    workflows:
    version: 2
    build_test_configure_and_deploy:
        jobs:
        - build_and_test:
            filters:
                branches:
                only: master
        - configure_and_deploy:
            requires:
                - build_and_test
            filters:
                branches:
                only: master

Dans un dossier ".circleci/config.yml
