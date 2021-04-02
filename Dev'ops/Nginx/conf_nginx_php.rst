server {
        listen 80 ;
        listen [::]:80 default_server;

        listen 443 ssl;

        ssl_certificate /etc/nginx/ssl/akarah-tld-cert.pem;
        ssl_certificate_key /etc/nginx/ssl/akarah-tld-key.pem;

        root /var/www/clickheat;
        server_name click.akarah.com;
        # Add index.php to the list if you are using PHP
        index index.php index.html index.htm index.nginx-debian.html;

        #location / {
        #       try_files $uri $uri/ =404;
        #}
        access_log      /var/log/nginx/clickheat.access.log;
        error_log       /var/log/nginx/clickheat.error.log;

        # change for your PHP version
        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/var/run/php/php7.3-fpm.sock;
        }

}
