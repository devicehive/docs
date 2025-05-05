---
title: "DeviceHive Plugin Management service"
slug: "devicehive-plugin-management-services"
excerpt: "This page contains basic information about Plugin Management service"
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Feb 27 2018 13:05:47 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2018 13:34:31 GMT+0000 (Coordinated Universal Time)"
---
# Overview

The plugin management service is an additional DeviceHive microservice, which allows managing device command or notification subscriptions into a dedicated Kafka topic. 

In order to register, delete, and update plugins, the plugin management service integrates with [Swagger](https://swagger.io/), which is a framework of API developer tools. 

The plugin supports various combinations of subscriptions: by networks, devices, or device types.

![](https://files.readme.io/a834dfa-Slide3.png "Slide3.png")

# Components

[Plugin Management service](https://github.com/devicehive/devicehive-java-server/tree/master/devicehive-plugin) – DeviceHive microservice which provides plugin information (JWT tokens, proxy endpoint, health check endpoint) after registration and also allows to update and delete plugin.

[Auth service](https://github.com/devicehive/devicehive-java-server/tree/master/devicehive-auth) – DeviceHive microservice for creating and refreshing user's and plugin's JWT tokens.

[WebSocket Kafka Proxy](https://github.com/devicehive/devicehive-ws-proxy) – Node.js service which wraps some of the essential message broker functionality allowing you to communicate with Apache Kafka through WebSockets. **Internal** instance establishes communication between DeviceHive microservices, **plugin** instance allows users to work with created plugins.

Kafka TOPIC_N – dedicated users topic with subscription messages (commands or notifications).

# Templates

Currently the following templates are available:  
[Java template](https://github.com/devicehive/devicehive-plugin-java-template) - a simple template which is meant to provide a sample structure for any DeviceHive plugins written in Java.  
[NodeJS plugin core functionality](https://github.com/devicehive/devicehive-plugin-core-node) which makes it possible to quickly and easily create DeviceHive plugins using NodeJS.  
[Python library](https://github.com/devicehive/devicehive-plugin-python) for building plugins - provides wrapper for DeviceHive plugin API  
[Cassandra storage plugin](https://github.com/devicehive/devicehive-plugin-cassandra-node) written in Node.js - allows you to store commands and notifications obtained through DeviceHive platform in Cassandra.  
[Kinesis Streaming plugin](https://github.com/devicehive/devicehive-plugin-kinesis-node) written in Node.js - allows you to stream data in Kinesis Data Streams and Firehose Delivery Streams as it goes through DeviceHive.
