## ANSIBLE

[Ansible docs](https://docs.ansible.com/ansible/latest/index.html)
[Ansible Galaxy](https://galaxy.ansible.com/)

Commande dans le vault
-------------------
i pour insertion
:wq pour enregistrer et quitter

Instalation
-------------------

COMMANDE GÉNÉRALE

    $ ansible localhost -m command -a "/bin/echo 'Hello Ansible'"
    $ ansible localhost -m ping
    $ ansible localhost -m composer -a "working_dir=./ no_dev=false"

HOSTING

créer un host : créer un fichier /ansible/hosts.ini ( base ci-dessous)

    ;--------------- ( IpV4 )
    	[local]
    		127.0.0.1
    		ansible_connection=local
    	[aws]
    	15.188.106.233 ansible_user=ubuntu ansible_ssh_private_key_file=Yohann-EC2.pem
    ;---------------

dans host.ini :

    ansible_ssh_common_args='-o StrictHostKeyChecking=no' // pour ne pas demander la vérification key ssh ( known_key )


ping sur un host :


	ansible 127.0.0.1 -m ping -i ansible/hosts.ini

Lister host(server) :


	ansible local --list-hosts -i ansible/hosts.ini


PLAYBOOK
-------------------

IMPORTANT
exécuter le playbook :


    $ ansible-playbook ansible/playbook.yml -i ansible/hosts.ini // exec le playbook sans vault
    $ ansible-playbook ansible/playbook.yml -i ansible/hosts.ini --ask-vault-pass // exécuter le playbook avec le vault
    $ ansible-vault rekey foo.yml // Recréer les variables vault
    $ ansible-vault view ansible/vars/vault.yml // Visualiser le vault
    $ ansible-vault edit ansible/vars/vault.yml // Editer le vault

DEBUGGAGE :
-------------------

deployment avec Nginx, si problème de 403 forbidden, voir/supprimer le défaut dans /etc/nginx/sites-enabled
Faire un composer install manuellement par SSH


Clonner un projet privé  :

-------------------

    vars_prompt:
      - name: "githubuser"
        prompt: "Enter your gitlab username"
        private: no
      - name: "githubpassword"
        prompt: "Enter your gitlab password"
        private: yes

    # 4 next step for clone repo git private
        - name: install pip3
          apt: name=python3-pip state=present

        - name: install pexpect #for clone
          pip:
            name: pexpect
          become: yes

        - name: delete old folders
          file:
            state: absent
            path: "{{ symfony_root_dir }}/"

        - name: Git clone
          expect:
            command: git clone https://gitlab.com/ozez/blitz.git "{{ symfony_root_dir }}"
            responses:
              Username: "{{ githubuser }}" # Username is a regex
              Password: "{{ githubpassword }}" # Password is a regex
            #no_log: true
