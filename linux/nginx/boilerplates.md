# nginx `.conf` boilerplates

### catch-all redirect for ip access:
redirect any visitors who try accessing your server via ip address to a domain of your choice.
```nginx
server {
  listen 80;
  listen [::]:80;
  server_name 5.5.5.5;
  return 301 https://domain.com;
}
```

### static html site
```nginx
server {
  listen 80;
  listen [::]:80;
  root /var/www/domain.com/public;
  index index.html index.htm;
  server_name domain.com www.domain.com;
  location / {
    try_files $uri $uri/ /index.html;
  }
}
```

### react app with react-router
```nginx
server {
  location / {
    try_files $uri $uri/ /index.html;
  }
}
```

### wordpress website
```nginx
server {
  listen 80;
  listen [::]:80;
  root /var/www/domain.com/public;
  index index.php index.html index.htm;
  server_name domain.com;

  location / {
    try_files $uri $uri/ /index.php?$args;
  }

  location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/run/php/php7.0-fpm.sock;
  }

  location ~ /\.ht {
    deny all;
  }
}
```

## production HTTPS static website

```
server {
  listen 80;
  listen [::]:80;
  server_name www.example.com;

  listen 443 ssl;
  ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
  ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;
  include /etc/letsencrypt/options-ssl-nginx.conf;

  return 301 https://example.com;
}

server {
  listen 80;
  listen [::]:80;

  root /var/www/example.com/public;

  index index.html index.htm;

  server_name example.com;

  location / {
    try_files $uri $uri/ /index.html;
  }

  listen 443 ssl;
  ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
  ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;
  include /etc/letsencrypt/options-ssl-nginx.conf;


  if ($scheme != "https") {
    return 301 https://$host$request_uri;
  }
}
```
