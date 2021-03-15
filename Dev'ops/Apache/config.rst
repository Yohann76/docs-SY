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
  

HTTPS:
( avec l'activation console : a2enmod ssl ) 
::

  # vhost https
  <VirtualHost *:443>
    DocumentRoot /var/www/webmail
    ServerName  webmail.mondomaine.com

    ServerSignature Off
    ErrorLog ${APACHE_LOG_DIR}/error_webmail.log      
    LogLevel info      
    CustomLog ${APACHE_LOG_DIR}/access_webmail.log combined      

    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/mailserver.crt
    SSLCertificateKeyFile /etc/ssl/private/mailserver.key
  </VirtualHost>
