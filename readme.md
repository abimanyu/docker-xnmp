# Docker XNMP Development
#### Cross-Platform (X), Nginx (N), MariaDB (M), PHP-FPM (P)
--- 

### How to
---

- install Docker https://www.docker.com/  
    `brew install docker`
- `docker network create xnmp-network`
- `docker-compose up`

---
Create default index pages  
: `./public_html/default/index.html`
```html
<!DOCTYPE html>  
<html>  
<head>  
	<title>DEFAULT DOMAIN</title>
    <style>
        body {
            background: black;
            color: hotpink;
        }
    </style>
</head>
<body>
	This is default domain
</body>
</html>
```

---
Create Nginx default configuration   
: `./nginx/enabled/default.conf`
```c#
server {
	listen 8080 default_server;
	listen [::]:8080 default_server;

	server_name _;

	index index.html index.htm;
	root /public_html/default;
	location / {
		# First attempt to serve request as file, then
		# as directory, then fall back to displaying a 404.
		try_files $uri $uri/ /index.php$is_args$args =404;
	}
}
```

