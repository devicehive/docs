---
title: "HTTPS configuration (SSL/TLS)"
slug: "https-configuration-ssltls"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Sep 15 2017 15:15:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
DeviceHive Frontend service doesn't provides connection encryption and relies on external service for that.

For Docker Compose installation we will use Compose feature to read configuration from [multiple Compose files](https://docs.docker.com/compose/extends/#multiple-compose-files). Second Compose file will start nginx reverse proxy with HTTPS support.

To configure secured HTTPS access to DeviceHive follow these steps.

1. Generate key and certificate signing request for your domain, sign CSR with Certificate Authority. Resulting certificate and key files must be in the PEM format.
2. Create ssl directory inside this directory and copy certificate, key and CA certificate chain files to it.
3. Generate dhparam file for nginx:

```text
openssl dhparam -out ssl/dhparam.pem 2048
```

4. Create nginx config file named nginx-ssl-proxy.conf. You can use provided example and edit certificate and key filenames:

```text
cp nginx-ssl-proxy.conf.example nginx-ssl-proxy.conf
vi nginx-ssl-proxy.conf
```

Note that ./ssl directory is mounted to /etc/ssl in container. So you need to edit only last part of path in ssl_certificate, ssl_certificate_key, ssl_trusted_certificate parameters.

5. Run DeviceHive with the following command:

```text
sudo docker-compose -f docker-compose.yml -f nginx-ssl-proxy.yml up -d
```

Or add line COMPOSE_FILE=docker-compose.yml:nginx-ssl-proxy.yml in .env file.

You can now access your DeviceHive API at <https://devicehive-host-url/api> and Admin Console at <https://devicehive-host-url/admin>.
