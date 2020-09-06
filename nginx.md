# Install NGINX debian

```
sudo apt-get install nginx
```

# Main commands

1. Restart nginx

```
sudo service nginx restart
```

1. Validate nginx config

```
/usr/nginx/sbin/nginx -tor/usr/nginx/sbin/nginx -t -c /usr/nginx/conf/nginx.conf
```

1. Nginx config reload without downtime

```
/usr/sbin/nginx -s reload
```

# Config file

/etc/nginx/sites-available/default

```
add_header X-Content-Type-Options nosniff;
add_header X-Frame-Options SAMEORIGIN;
add_header X-XSS-Protection "1; mode=block";
add_header Content-Security-Policy "frame-ancestors 'self'";

server {
        listen 80 default_server;
        listen [::]:80 default_server;
        gzip on;
        gzip_vary on;
        gzip_min_length 1240;
        gzip_proxied expired no-cache no-store private auth;
        gzip_types text/plain text/css text/xml text/javascript application/x-javascript application/xml;
        gzip_disable "MSIE [1-6]\.";
        root /usr/share/nginx/html;
        # Add index.php to the list if you are using PHP
        index index.html index.htm;
        server_name _;
        location ~*  \.(jpg|jpeg|png|gif|ico|css|js)$ {
                expires 365d;
        }
        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                #try_files $uri $uri/ =404;
                if (!-e $request_filename){
                         rewrite ^(.*)$ /index.html break;
                }
        }
 }
```

## Redirection http to https

```
server {
        listen 80;
        listen [::]:80;
        server_name test.com;
        return 301 https://$host:8084/$request_uri;
}
```

## HTTPS

```
server {
        listen 443 ssl;
        listen [::]:443 ssl;
        server_name test.com;
          ssl_certificate     /home/test/ssl/test.pem;
          ssl_certificate_key /home/test/ssl/test.key;
          ssl_protocols       TLSv1 TLSv1.1 TLSv1.2;
          ssl_ciphers         HIGH:!aNULL:!MD5;
}
```

## GZIP compression

```
server {
        gzip on;
        gzip_vary on;
        gzip_min_length 1240;
        gzip_proxied expired no-cache no-store private auth;
        gzip_types text/plain text/css text/xml text/javascript application/x-javascript application/xml;
        gzip_disable "MSIE [1-6]\.";
}
```

## Security HTTP Headers to Prevent Vulnerabilities

Add outside of server

```
add_header X-Content-Type-Options nosniff;
add_header X-Frame-Options SAMEORIGIN;
add_header X-XSS-Protection "1; mode=block";
add_header Content-Security-Policy "frame-ancestors 'self'";
```

1. X-XSS-Protection

```
add_header X-XSS-Protection "1; mode=block";
```

1. HTTP Strict Transport Security

HSTS (HTTP Strict Transport Security) header to ensure all communication from a browser is sent over HTTPS (HTTP Secure). This prevents HTTPS click through prompts and redirects HTTP requests to HTTPS.

Before implementing this header, you must ensure all your website page is accessible over HTTPS else they will be blocked.

add_header Strict-Transport-Security ‘max-age=31536000; includeSubDomains; preload’;

1. X-Frame-Options

Use X-Frame-Options header to prevent Clickjacking vulnerability on your website. By implementing this header, you instruct the browser not to embed your web page in frame/iframe. This has some limitation in browser support, so you got to check before implementing it.

add_header X-Frame-Options SAMEORIGIN;

SAMEORIGIN - Frame/iframe of content is only allowed from the same site origin.

1. X-Content-Type-Options

add_header X-Content-Type-Options nosniff;

Prevent MIME types security risk by adding this header to your web page’s HTTP response. Having this header instruct browser to consider files types as defined and disallow content sniffing. There is only one parameter you got to add “nosniff”.

1. Content Security Policy

Prevent XSS, clickjacking, code injection attacks by implementing the Content Security Policy (CSP) header in your web page HTTP response.

add_header Content-Security-Policy “default-src ‘self’;”;

https://geekflare.com/http-header-implementation/

## Setting up Nginx reverse proxy

```
location / {
        proxy_pass http://1.1.1.1:8083;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
 }
```

Redirect test.com/api to http://localhost:8090/

```
location /api {
    rewrite ^/api/?(.*) /$1 break;
    proxy_pass http://localhost:8090/;
}
```

## Nginx + php

Install php

```
sudo apt-get install php-fpm php-mysql
```

```
server {
        listen 80;
        listen [::]:80;
        server_name test.com www.test.com;
        root /var/www;
        index index.html index.htm index.nginx-debian.htm index.php;
        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                try_files $uri $uri/ =404;
        }
        location ~ \.php$ {
            try_files $uri /index.php =404;
            fastcgi_split_path_info ^(.+\.php)(/.+)$;
            fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
            fastcgi_index index.php;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            include fastcgi_params;
        }
}
```

https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-in-ubuntu-16-04

## Restrict by ip

```
location / {
                allow 202.83.225.118;
                deny all; # Deny everyone else
}
```

## Using nginx as HTTP load balancer

Default load balancing configuration

```
http {
    upstream myapp1 {
        server srv1.example.com;
        server srv2.example.com;
        server srv3.example.com;
    }

    server {
        listen 80;

        location / {
            proxy_pass http://myapp1;
        }
    }
}
```

http://nginx.org/en/docs/http/load_balancing.html

## Logging Settings

```
access_log /var/log/nginx/access.log;
    error_log /var/log/nginx/error.log;
```

## WAF

1. NAXSI

https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-naxsi-on-ubuntu-16-04

1. ModSecurity v3

https://malware.expert/howto/how-to-install-nginx-with-modsecurity-v3-0/
