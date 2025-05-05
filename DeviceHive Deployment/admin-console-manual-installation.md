---
title: "Admin console manual installation"
slug: "admin-console-manual-installation"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Feb 07 2018 08:59:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Feb 07 2018 09:37:10 GMT+0000 (Coordinated Universal Time)"
---
# Overview

It might worth running DeviceHive Admin panel manually if you want to customize it for your own purposes. Below you can find detailed instructions on that.

# Prerequisites

## Configure Admin console source code

- `git clone https://github.com/devicehive/devicehive-admin-console.git` 
- cd devicehive-admin-console/scripts/
- Update `config.js` file with your values, for example:

```
restEndpoint: '{DH_HOST}:8080/dh/rest'
rootUrl: '/'
authRestEndpoint: '{DH_HOST}:8090/dh/rest'
```

## Configure Nginx

- Install [Nginx](https://www.nginx.com/) using official [instructions](https://www.nginx.com/resources/wiki/start/topics/tutorials/install/).
- Make changes in nginx config file (`/usr/local/etc/nginx/nginx.conf` or similar)

```
events { worker_connections 60000; }

http {

    tcp_nodelay on;
    tcp_nopush on;

    include /usr/local/etc/nginx/mime.types;
    default_type  application/octet-stream;
    gzip              on;
    gzip_http_version 1.0;
    gzip_proxied      any;
    gzip_min_length   500;
    gzip_disable      "MSIE [1-6]\.";
    gzip_types        text/plain text/xml text/css
                      text/comma-separated-values
                      text/javascript
                      application/x-javascript
                      application/atom+xml;

    server {
        listen       8081;
        port_in_redirect off;
        location / {
            sendfile on;
            root {PATH_TO_ADMIN_CONSOLE};
            index index.html;
        }
    }
}
```

# Run

Start nginx and discover DeivceHive Admin console at  
`http://localhost:8081`

Default admin user credentials: 

```
login = dhadmin
password = dhadmin_#911
```

Enjoy!
