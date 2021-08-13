this is a nginx configuration

## Reload nginx

    $ nginx -t && service nginx reload
    $ sudo service start nginx

## install a SSL certificate :
in etc/nginx/sites-available

    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    ssl on;
    ssl_certificate     /etc/nginx/ssl/yourdomain-tld-cert.pem;
    ssl_certificate_key    /etc/nginx/ssl/yourdomain-tld-key.pem;
