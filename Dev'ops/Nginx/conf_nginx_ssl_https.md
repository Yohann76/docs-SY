		server {
		    listen 443 ssl;
		    server_name www.akarah.com;

		    ssl_certificate /etc/nginx/ssl/cloudflare/cloudflare_certificate.pem;
		    ssl_certificate_key /etc/nginx/ssl/cloudflare/cloudflare_certificate.key;

		    return 301 https://akarah.com$request_uri;
		}

		server {
			listen 80;
			listen 443 ssl;

			ssl_certificate /etc/nginx/ssl/cloudflare/cloudflare_certificate.pem;
			ssl_certificate_key /etc/nginx/ssl/cloudflare/cloudflare_certificate.key;

			server_name akarah.com;

			index index.php index.html index.htm;
			#autoindex on;

			if ($scheme = http) {
					return 301 https://$server_name$request_uri;
			}

			access_log      /var/log/nginx/akarah.access.log;
			error_log       /var/log/nginx/akarah.error.log;


			gzip on;
			gzip_proxied any;
			gzip_comp_level 4;
			gzip_types text/css application/javascript image/svg+xml;


			proxy_http_version 1.1;
			proxy_set_header Upgrade $http_upgrade;
			proxy_set_header Connection 'upgrade';
			proxy_set_header Host $host;
			proxy_cache_bypass $http_upgrade;


			location /_next/static {
					proxy_pass http://localhost:3000;
			}


			location /static {
					proxy_pass http://localhost:3000;
			}


			location / {
					proxy_pass http://localhost:3000;
			}

			location ~ /\.ht {
					deny all;
			}
		}
