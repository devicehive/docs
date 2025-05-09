---
title: "Deployment with Docker"
slug: "deployment-with-docker"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Jul 13 2015 09:27:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 09:53:19 GMT+0000 (Coordinated Universal Time)"
---
# Overview

The easiest way to try DeviceHive locally or in your development datacenter is to deploy it using [Docker Compose](https://docs.docker.com/compose/).

This will start following basic DeviceHive services:

- DeviceHive Frontend service
- DeviceHive Backend service
- DeviceHive Auth service
- DeviceHive Admin Console
- DeviceHive Websocket Proxy
- [DeviceHive Nginx Proxy](https://nginx.org/en/)
- [Kafka](https://kafka.apache.org/)
- [PostgreSQL](https://www.postgresql.org/)
- [Hazelcast IMDG](https://hazelcast.com/use-cases/imdg/)

# Prerequisites

- Install [Docker Compose](https://docs.docker.com/compose/) using official [instructions](https://docs.docker.com/compose/install/). 
- `git clone https://github.com/devicehive/devicehive-docker.git` 
- cd rdbms-image

## Before you start

DeviceHive can be started without any additional configuration, `docker-compose.yml` file contains all necessary parameters set to safe defaults. Though there is one parameter that could and should be changed due to security reasons - **JWT_SECRET**.  
DeviceHive ecosystem uses JWT tokens for authentication. **JWT_SECRET** is used for signing JWT tokens and is generated at startup of DeviceHive and stored in the database. You can change it by exporting the **JWT_SECRET** environment variable or by adding `JWT_SECRET=<your value>` line in the `.env` file inside current directory.

# Run

In order to run DeviceHive stack on top of Docker containers, define environment variables as per your requirements and run:

```
sudo docker-compose up -d
```

After a while (1-2 minutes) you should be able to access your DeviceHive micro services via endpoints described in the next section.

## Additional services

### DeviceHive Plugin management service

There's a huge amount of business cases which DeviceHive ecosystem can not cover from the scratch. For example, you may want to implement alerting in case of some emergency. Or to store sensor data outside, in AWS S3 or Cassandra. That's why Plugin management service were designed and developed. It allows to create your own simple consumers of notifications and commands, implement custom behavior with the Node.js, Python or Java templates and run as a separate process inside Docker container or as a Kubernetes pod.

To enable optional DeviceHive Plugin management service start docker-compose with the following command:

```
sudo docker-compose -f docker-compose.yml -f dh_plugin.yml up -d
```

Or add line `COMPOSE_FILE=docker-compose.yml:dh_plugin.yml` in `.env` file.

### DeviceHive MQTT plugin

The DeviceHive MQTT plugin is MQTT transport layer between MQTT clients and DeviceHive server. The broker uses WebSocket sessions to communicate with DeviceHive Server and Redis server for persistence functionality.

To enable optional DeviceHive MQTT brokers run DeviceHive with the following command. This will start MQTT brokers on port 1883 and internal Redis container:

```
sudo docker-compose -f docker-compose.yml -f mqtt-brokers.yml
```

Or add line `COMPOSE_FILE=docker-compose.yml:mqtt-brokers.yml` in `.env` file.

### DeviceHive Grafana Datasource

This datasource was created to connect Grafana with DeviceHive to track commands and notifications by particular device. To enable optional Grafana service with DeviceHive datasource run DeviceHive with the following command:

```
sudo docker-compose -f docker-compose.yml -f grafana.yml up -d
```

Or add line `COMPOSE_FILE=docker-compose.yml:grafana.yml` in `.env` file.

This only adds Grafana container. After that you need to install plugin in it:

```
sudo docker-compose exec grafana bash -c 'grafana-cli plugins install devicehive-devicehive-datasource'
sudo docker-compose down
sudo docker-compose up
```

Grafana will be available at `http://<devicehive-host>/grafana` with default Grafana credentials. 

## Service endpoints

Table below lists endpoints where you can find various DeviceHive services. Replace `localhost` with actual hostname of the docker daemon and start observing DeviceHive capabilities.

| Service                | URL                              |
| :--------------------- | :------------------------------- |
| Admin Console          | http\://localhost/admin          |
| Frontend service API   | http\://localhost/api/rest       |
| Auth service API       | http\://localhost/auth/rest      |
| Plugin service API     | http\://localhost/plugin/rest    |
| Frontend Swagger       | http\://localhost/api/swagger    |
| Auth Swagger           | http\://localhost/auth/swagger   |
| Plugin Swagger         | http\://localhost/plugin/swagger |
| Grafana                | http\://localhost/grafana        |
| Plugin websocket proxy | ws://localhost/plugin/proxy      |
| MQTT brocker           | mqtt://localhost:1883            |

## Exposed ports

| Port   | Service          | Notes                                                                                                    |
| :----- | :--------------- | :------------------------------------------------------------------------------------------------------- |
| 80,443 | Nginx proxy      | Primary port for all services                                                                            |
| 1883   | MQTT brokers     | If enabled, see [MQTT plugin](#section-devicehive-mqtt-plugin) section above                             |
| 2181   | Zookeeper        |                                                                                                          |
| 5432   | PostgreSQL       |                                                                                                          |
| 5701   | Hazelcast        |                                                                                                          |
| 7071   | Kafka metrics    | If enabled, see [Kafka metrics](#kafka-metrics) section below                                            |
| 8080   | Frontend service |                                                                                                          |
| 8090   | Auth service     |                                                                                                          |
| 8110   | Plugin service   | If enabled, see [Plugin management service](#section-devicehive-plugin-management-service) section above |
| 9092   | Kafka            |                                                                                                          |
| 9395   | cAdvisor         | If enabled, see [cAdvisor metrics](#section-cadvisor-metrics) section below                              |
| 3000   | Grafana          | If enabled, see [Grafana datasource](doc:grafana-datasource) section above                               |

## Development run

In order to run only DeviceHive 3d-party dependencies in Docker containers, simply run:

### For PROXY version of Devicehive services:

```
sudo docker-compose -f dev-proxy.yml up -d
```

### For RPC version of Devicehive services:

```
sudo docker-compose -f dev-rpc.yml up -d
```

Then you'd be able to start all DeviceHive java services (backend, frontend, auth, plugin manager) by running `java -jar devicehive-...-boot.jar`

## Configuration

All containers are configured via environment variables and Docker Compose can pass variables from its environment to containers or read them from [.env](https://docs.docker.com/compose/compose-file/#env_file) file. To make persistent configuration changes we will add parameters in the `.env` file in the current directory.

### JWT secret

- `JWT_SECRET` - changes the randomly generated JWT signing secret.

### DeviceHive image tags

Released versions of devicehive-docker use stable DeviceHive images from [DeviceHive Docker Hub repository](https://hub.docker.com/u/devicehive/). But if you want follow DeviceHive development add following parameters:

- `DH_TAG` - tag for DeviceHive [Frontend](https://hub.docker.com/r/devicehive/devicehive-frontend/), [Backend](https://hub.docker.com/r/devicehive/devicehive-backend/) and [Hazelcast](https://hub.docker.com/r/devicehive/devicehive-hazelcast/) images. Can be set to `development` to track development version of DeviceHive.
- `DH_ADMIN_TAG` - tag for DeviceHive [Admin Console](https://hub.docker.com/r/devicehive/admin-console/) image. Can be set to `development` to track development version of Admin Console.

### PostgreSQL

These variables are used by Frontend, Backend and PostgreSQL containers.

- `DH_POSTGRES_ADDRESS` - Address of PostgreSQL server instance. Defaults to `postgres`, which is address of internal PostgreSQL container.
- `DH_POSTGRES_PORT` - Port of PostgreSQL server instance, defaults to `5432` if undefined.
- `DH_POSTGRES_DB` - PostgreSQL database name for DeviceHive metadata. It is assumed that database already exists and either blank or has been initialized by DeviceHive. Defaults to `postgres`.
- `DH_POSTGRES_USERNAME` and `DH_POSTGRES_PASSWORD` - login/password for DeviceHive user in PostgreSQL that have full access to `DH_POSTGRES_DB`. Defaults are `postgres` and `mysecretpassword`.

### Kafka

To enable DeviceHive to communicate over Apache Kafka message bus to scale out and interoperate with other componets, such us Apache Spark, or to enable support of Apache Cassandra for fast and scalable storage of device messages define the following environment variables:

- `DH_ZH_ADDRESS` - Comma-separated list of addressed of ZooKeeper instances. Defaults to `zookeeper`, which is address of internal Zookeeper container.
- `DH_ZK_PORT` - Port of ZooKeeper instances, defaults to `2181` if undefined.
- `DH_KAFKA_BOOTSTRAP_SERVERS` -  Comma separated list of Kafka servers, i.e. `host1:9092,host2:9092,host3:9092`. This parameter or `DH_KAFKA_ADDRESS` is required to be set.
- `DH_KAFKA_ADDRESS` - Address of Apache Kafka broker node. Mutually exclusive with `DH_KAFKA_BOOTSTRAP_SERVERS` parameter.
- `DH_KAFKA_PORT` - Port of Apache Kafka broker node, defaults to `9092` if undefined. Ignored if `DH_KAFKA_ADDRESS` is undefined.
- `DH_RPC_SERVER_REQ_CONS_THREADS` - Kafka request consumer threads in the Backend, defaults to `3` if undefined.
- `DH_RPC_SERVER_WORKER_THREADS` - Server worker threads in the Backend, defaults to `3` if undefined. On machine with many CPU cores and high load this value must be raised. For example on machine with 8 core it must be set to `6`.
- `DH_RPC_CLIENT_RES_CONS_THREADS` - Kafka response consumer threads in the Frontend, defaults to `3`.
- `DH_FE_SPRING_PROFILES_ACTIVE`, `DH_BE_SPRING_PROFILES_ACTIVE` and `DH_PLUGIN_SPRING_PROFILES_ACTIVE` - Changes which Spring profile use for Frontend, Backend and Plugin sevices respectively. Defaults to `ws-kafka-proxy-frontend` for Frontend, `ws-kafka-proxy-backend` for Backend and `ws-kafka-proxy` for Plugin. Can be changed to `rpc-client` for Frontend/Plugin and `rpc-server` for Backend to use direct connection to Kafka instead of devicehive-ws-proxy service.

### Logging

By default DeviceHive writes minimum logs for better performance. Two configuration parameters are supported:

- `DH_LOG_LEVEL` - log verbosity for DeviceHive Java classes. Defaults to `INFO` for both devicehive-frontend and devicehive-backend.
- `ROOT_LOG_LEVEL` - log verbosity for external dependencies. Defaults to `WARN` for devicehive-frontend and `INFO` for devicehive-backend.

Possible values are: `TRACE`, `DEBUG`, `INFO`, `WARN`, `ERROR`.

You can find more configurable parameters in [frontend][fe-script-url] and [backend][be-script-url] startup scripts.

[fe-script-url]: https://github.com/devicehive/devicehive-java-server/blob/master/dockerfiles/devicehive-frontend/devicehive-start.sh

[be-script-url]: https://github.com/devicehive/devicehive-java-server/blob/master/dockerfiles/devicehive-backend/devicehive-start.sh

## HTTPS configuration (TLS)

DeviceHive Proxy provides TLS support by default. If custom certificate is not configured it generates self-signed certificate and stores them in `dh-proxy-ssl` Docker volume.

### Using custom certificate

For Docker Compose installation we will use Compose feature to read configuration from [multiple Compose files](https://docs.docker.com/compose/extends/#multiple-compose-files). Second Compose file will start devicehive-proxy container with custom certificate.  
To configure DeviceHive Proxy to use your own certificate follow next steps:

1. Generate key and certificate signing request for your domain, sign CSR with Certificate Authority. Resulting certificate and key files must be in the PEM format.
2. Create `ssl` directory outside of `devicehive-docker` directory, on the same level.
3. Generate dhparam file for nginx:

```
openssl dhparam -out ssl/dhparam.pem 2048
```

4. Copy SSL certificate to `ssl` directory. File must be named `ssl_certificate`.
5. Copy SSL certificate key to `ssl` directory. File must be named `ssl_certificate_key`.
6. Run DeviceHive with the following command:

```
sudo docker-compose -f docker-compose.yml -f dh_proxy_custom_certificate.yml up -d
```

Or add line `COMPOSE_FILE=docker-compose.yml:dh_proxy_custom_certificate.yml` in `.env` file.

You can now access your DeviceHive API at https\://devicehive-host-url/api and Admin Console at https\://devicehive-host-url/admin.

## Monitoring

### cAdvisor metrics

We provide Compose file with cAdvisor service which exports various container-related metrics. It's exposed on port 9395.

Run DeviceHive with the following command:

```
sudo docker-compose -f docker-compose.yml -f cadvisor.yml
```

Or add line `COMPOSE_FILE=docker-compose.yml:cadvisor.yml` in `.env` file.

### Kafka metrics

You can start Kafka service with additional Prometheus metrics exporter. Necessary parameters for Kafka container are already configured in `devicehive-metrics.yml` file. It will launch JMX exporter on tcp port 7071.

Run DeviceHive with the following command:

```
sudo docker-compose -f docker-compose.yml -f devicehive-metrics.yml
```

Or add line `COMPOSE_FILE=docker-compose.yml:devicehive-metrics.yml` in `.env` file.

Related Prometheus config for this exporter and link to Grafana Dashboard is in the [Monitoring Kafka with Prometheus](https://www.robustperception.io/monitoring-kafka-with-prometheus/) blog post by Prometheus developer.

## Development environment

### Using CI images

Continuous Integration system uploads images built from every branch to [devicehiveci](https://hub.docker.com/r/devicehiveci/) repository on Docker Hub.  
To use these images add `ci-images.yml` to `COMPOSE_FILE` parameter in `.env` file. If you don't have this parameter in `.env` file, add it like that:

```
COMPOSE_FILE=docker-compose.yml:ci-images.yml
```

### Debugging

DeviceHive Frontend and Backend services can be run with remote JMX connection enabled. TCP ports 9999-10002 must be open on a firewall.

1. Create `jmxremote.password` and `jmxremote.access` file in the current directory. `jmxremote.password` must be readable by owner only. For example, if you want to grant JMX access for user 'developer' with password 'devpass', create these files like that:

```
echo "developer devpass" > jmxremote.password
echo "developer readwrite" > jmxremote.access

chmod 0400 jmxremote.password
```

2. Open `jmx-remote.yml` file and replace `<external hostname>` in \_JAVA_OPTIONS env vars with actual hostname of DeviceHive server.
3. Run DeviceHive with the following command:

```
sudo docker-compose -f docker-compose.yml -f jmx-remote.yml
```

Or add line `COMPOSE_FILE=docker-compose.yml:jmx-remote.yml` in `.env` file.

### Hazelcast Management Center

You can launch Management Center to monitor Hazelcast usage and health. TCP port 9980 must be open on a firewall.

1. Add `hazelcast-management-center.yml` to `COMPOSE_FILE` parameter in `.env` file. If you don't have this parameter in `.env` file, add it like that:

```
COMPOSE_FILE=docker-compose.yml:hazelcast-management-center.yml
```

2. Run DeviceHive as usual.
3. Open Hazelcast Management Center in browser via http\://devicehive-server:9980/mancenter. You'll be required to configure authentication on the first launch.

## Backup and restore

### Backup PostgreSQL database

To backup database use following command:

```
sudo docker-compose exec postgres sh -c 'pg_dump --no-owner -c -U ${POSTGRES_USER} ${POSTGRES_DB}' > dump_`date +%d-%m-%Y"_"%H_%M_%S`.sql
```

This will create dump\_\*.sql file in the current directory.

### Restore PostgreSQL database

To restore database from SQL dump file delete existing database (if any), start only postgres container and pass dump file contents to psql utility in container:

```
sudo docker-compose down
sudo docker volume ls -q|grep devicehive-db| xargs sudo docker volume rm
sudo docker-compose up -d postgres
cat dump_*.sql | sudo docker exec -i rdbmsimage_postgres_1 sh -c 'psql -U ${POSTGRES_USER} ${POSTGRES_DB}'
sudo docker-compose up -d
```

# Docker Host configuration

Example configuration steps for CentOS 7.3 to became Docker host:

1. Install CentOS 7.3, update it and reboot.
2. Install docker-latest package:

```
sudo yum install -y docker-latest
```

3. Configure Docker to use LVM-direct storage backend. These steps are required for better disk IO performance:

   1. Add new disk with at least 10 GB of disk space. It will be used as physical volume for Docker volume group.
   2. Add following lines to `/etc/sysconfig/docker-latest-storage-setup` files. Change `/dev/xvdb` for you device.

   ```
   VG=docker
   DEVS=/dev/xvdb
   ```

   3. Run storage configuration utility

   ```
   sudo docker-latest-storage-setup
   ```
4. Enable and start Docker service:

```
sudo systemctl enable docker-latest
sudo systemctl start docker-latest
```

5. Install docker-compose:

   1. Install and update python-pip package manager:

   ```
   sudo yum install -y python2-pip
   sudo pip install -U pip
   ```

   2. Install docker-compose:

   ```
   pip install docker-compose
   ```

Enjoy!
