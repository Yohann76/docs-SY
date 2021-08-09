## BlackFire

[Blackfire Docs](https://blackfire.io/docs/introduction)

Instalation Windows
-------------------

[windows blackfire Instalation](https://blackfire.io/docs/up-and-running/installation)

Config Wamp
-----------


  [blackfire]
  ;extension=C:\wamp64\bin\php\php7.3.12\ext\blackfire-php-windows_x64-php-73_nts.dll
  extension=C:\wamp64\bin\php\php7.3.12\ext\blackfire-php-windows_x64-php-73.dll
  blackfire.agent_timeout = 0.25

  ;extension=blackfire.dll
  ;blackfire.agent_timeout = 0.25
  blackfire.log_file = /tmp/blackfire.log
  blackfire.log_level = 4
  BLACKFIRE_AGENT_SOCKET="tcp://127.0.0.1:8307"

Commande
=========

Profiler :

    blackfire curl http://developpement/Formation%20PHP%20Symfony/Projet%208%20TodoList/TodoList/public/

configuration pre-requis
--------------------------

- installer curl
- deplacer les dll dans le dossier wamp64/bin/php/php7.3.12/ext/fihier.dll (preconiser sans extension nts)
- reproduire la configuration cité plus haut dans le php.ini de php et également celui d'apache


Mettre a jour les configuration:
------------------------------
Sacha

     **Configuration de l'agent:**
     blackfire-agent --register --server-id=956c89f4-db87-4af3-b1ab-26fd386a49ed --server-token=aad82f78061aa8f204d53d29f56751481af094215884832fb767a2dcdb18336c

    **Configuration du client probe:**
    blackfire config --client-id=323c48dc-fe0d-421a-88af-75e9667426f4 --client-token=fe00b07da92104532542352ab0ec5ed188215046febb17310ce79c15a0880d4d

    maj: blackfire config --dump      // blackfire curl https://gitlist.demo.blackfire.io/

Yohann

    **Configuration de l'agent:**
    blackfire-agent.exe --register --server-id=c54c0b78-b554-4456-b4e2-df00a33081c0 --server-token=7cedc10841baebac26f47b2aff5cdfad9b1e25abe1affc4cee3a1323826d2647
    sudo /etc/init.d/blackfire-agent restart // restart agent
    **Configuration du client probe:**
    blackfire config --client-id=b584c08a-b27a-4ad0-bed9-d130a93450de --client-token=a72fb8e56b5513d8c9f689b80a6a9d485664b1be762f4783cc695c681604d1f6

profiler :


    **Lancer l'agent**
    blackfire-agent.exe
    ** lancé l'extension de Google chrome


Source d'érreur :

Verifier que l'extension php est présente et activé et a jours dans WAMP
Verifier les droits des fichiers ( que l'agent soit accessible )
Verifier les bon token/id client et server ( dans l'agents  -> server token/id et dans les variable d'environement -> client token/id )
L'agent doit etre dans Programme Data pour avoir les droits
Vérifier que l'agent est bien détécter sur la docs de blackfire
