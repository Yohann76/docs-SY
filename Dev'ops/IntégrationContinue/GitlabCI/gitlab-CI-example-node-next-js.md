## Gitlab CI Example ( Sacha maintener )


Config GitlabCI pour config node-next-js sur une machine debian
-------------------


    image: akarah/node-next-js
    #configuration for debian server

    npm:

      # Same stage as `composer` so that they run in parallel.
      stage: build

      only:
        - preprod
        - master

      # Cache the `node_modules` folder
      # using the `npm` suffix on the key.
      #cache:
        #key: ${CI_COMMIT_REF_SLUG}-npm
        #paths:
          #- node_modules/

      before_script :
        - npm cache clean -f

      # Install and compile.
      script:
        - npm install
        - NODE_ENV=production npm run build

      # Provide the other jobs of the pipeline with
      # the node dependencies and the compiled assets.
      artifacts:
        expire_in: 1 day
        paths:
          - .next/
          - node_modules/

    # echo 'ssh-rsa AAAAB3NzaSGMFZW7yB anask@mahineA'  >> ~/.ssh/authorized_keys
    # echo "$SSH_PRIVATE_KEY" | tr -d '\r' | ssh-add - > /dev/null
    .init_ssh: &init_ssh |
      eval $(ssh-agent -s)
      echo "$SSH_PRIVATE_KEY" | tr -d '\r' | ssh-add - > /dev/null
      mkdir -p ~/.ssh
      chmod 700 ~/.ssh
      ssh-keyscan 51.178.95.96 >> ~/.ssh/known_hosts
      chmod 644 ~/.ssh/known_hosts



    # sudo -u deployer -H ssh-copy-id deployer@51.178.95.96
    # ssh-copy-id deployer@51.178.95.96

    prod_mercure:

      #variables:
        #CI_DEBUG_TRACE: "true"

      stage: deploy
      script:
        - *init_ssh # This is pretty convenient now.
        #- ssh -p22 deployer@51.178.95.96 "cd /var/www/next-wikirun && git remote set-url --push origin git@gitlab:$CI_PROJECT_PATH"
        - ssh -p22 git@51.178.95.96 "cd /var/www/next-wikirun && ls"
        - ssh -p22 git@51.178.95.96 "cd /var/www/next-wikirun && rm -Rf public"
        - ssh -p22 git@51.178.95.96 "cd /var/www/next-wikirun && git reset --hard HEAD"
        - ssh -p22 git@51.178.95.96 "cd /var/www/next-wikirun && git pull origin master"
        - ssh -p22 git@51.178.95.96 "cd /var/www/next-wikirun && npm install --production"
        - ssh -p22 git@51.178.95.96 "cd /var/www/next-wikirun && pm2 start"
        #- ssh -p22 git@51.178.95.96 "cd /var/www/next-wikirun && pkill -f node"

        #- ssh -p22 git@51.178.95.96 "cd /var/www/next-wikirun && npm run build"

        #- ssh -p22 git@51.178.95.96 "cd /var/www/next-wikirun && npm run start"

        # pkill -f node
        # kill -9
        #run start -- -p 443

        #- ssh -p22 git@51.178.95.96 "cd /var/www/next-wikirun && rm -rf public/*"
        #- ssh -p22 git@51.178.95.96 "cd /var/www/next-wikirun && mv out/* public"
        #- ssh -p22 git@51.178.95.96 "cd /var/www/next-wikirun && npm run start"

      environment:
        name: production
        url: 51.178.95.96

      only:
        - master
      # Do not run automatically.
      # Wait for a human to click on play.
      when: manual
