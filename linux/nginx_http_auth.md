# http auth via .htpasswd on nginx

### install apache2-utils:
```bash
sudo apt-get install apache2-utils
```

### check for existing .htpasswd:
```bash
sudo cat /etc/nginx/.htpasswd
```

### create .htpasswd:
```bash
sudo htpasswd -c /etc/nginx/.htpasswd USERNAME
```

### add to existing .htpasswd:
```bash
sudo htpasswd /etc/nginx/.htpasswd USERNAME
```

### add to nginx configuration (.conf):
```nginx
server {
  location / {
    auth_basic "Restricted Content";
    auth_basic_user_file /etc/nginx/.htpasswd;
  }
}
```

### reload nginx:
```bash
sudo systemctl reload nginx
```
