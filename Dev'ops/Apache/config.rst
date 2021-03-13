dossier de configuration :
::

  /etc/apache2/sites-enabled/

::

  <VirtualHost 172.20.30.40>
      # serveur virtuel primaire
      DocumentRoot "/www/subdomain"
      RewriteEngine On
      RewriteRule "." "/www/subdomain/index.html"
      # ...
  </VirtualHost>
  
  
Réécrire une URL : 
::
  
  Alias "/url" "/urlNext"
