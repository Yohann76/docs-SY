## Workflow


[Workflow docs](https://symfony.com/doc/current/workflow.html)


    $ composer require symfony/workflow


# config : 

    # config/packages/workflow.yaml
    framework:
        workflows:
            blog_publishing:
                type: 'workflow' # or 'state_machine'
                audit_trail:
                    enabled: true
                marking_store:
                    type: 'method'
                    property: 'currentPlace'
                supports:
                    - App\Entity\BlogPost
                initial_marking: draft
                places:
                    - draft
                    - reviewed
                    - rejected
                    - published
                transitions:
                    to_review:
                        from: draft
                        to:   reviewed
                    publish:
                        from: reviewed
                        to:   published
                    reject:
                        from: reviewed
                        to:   rejected
