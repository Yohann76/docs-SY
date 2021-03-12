::

  <VirtualHost 172.20.30.40>
      # serveur virtuel primaire
      DocumentRoot "/www/subdomain"
      RewriteEngine On
      RewriteRule "." "/www/subdomain/index.html"
      # ...
  </VirtualHost>
