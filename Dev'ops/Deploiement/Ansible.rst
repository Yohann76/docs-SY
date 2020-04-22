.. index::
   single: Ansible; 

ANSIBLE : 
===================

`Ansible docs`_
`Ansible Galaxy`_

Instalation
-------------------


COMMANDE GÉNÉRALE
ansible localhost -m command -a "/bin/echo 'Hello Ansible'"
ansible localhost -m ping
ansible localhost -m composer -a "working_dir=./ no_dev=false"

HOSTING 

créer un host : créer un fichier /ansible/hosts.ini ( base ci-dessous) 
::

;--------------- ( IpV4 ) 
	[local]
		127.0.0.1
		ansible_connection=local
	[aws]  
	15.188.106.233 ansible_user=ubuntu ansible_ssh_private_key_file=Yohann-EC2.pem
;---------------
ping sur un host :
::

	ansible 127.0.0.1 -m ping -i ansible/hosts.ini

Lister host(server) : 
::

	ansible local --list-hosts -i ansible/hosts.ini



PLAYBOOK
-------------------

IMPORTANT
exécuter le playbook : 
::

	ansible-playbook ansible/playbook.yml -i ansible/hosts.ini

exécuter le playbook avec le vault :
::

	ansible-playbook ansible/playbook.yml -i ansible/hosts.ini --ask-vault-pass

Recréer les variables vault :
::

	ansible-vault rekey foo.yml


Visualiser le vault :
::

	ansible-vault view ansible/vars/vault.yml

Editer le vault :
::

	ansible-vault edit ansible/vars/vault.yml



DEBUGGAGE : 
-------------------

deployment avec Nginx, si problème de 403 forbidden, voir/supprimer le défaut dans /etc/nginx/sites-enabled 
Faire un composer install manuellement par SSH 


.. _`Ansible docs`: https://docs.ansible.com/ansible/latest/index.html
.. _`Ansible Galaxy`: https://galaxy.ansible.com/
	