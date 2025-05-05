---
title: "Security in DeviceHive"
slug: "security-in-devicehive"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Sep 05 2017 18:40:34 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 15 2018 15:07:56 GMT+0000 (Coordinated Universal Time)"
---
In DeviceHive we care about keeping things secure and safe.

DeviceHive authentication is secured by JSON Web Tokens (JWT). The key benefits of this approach are:

- Token is stateless and self contained, no need to store on server side;
- Portability - one token can be used with multiple backends;
- Reduce compute and network round time;
- Decentralized, can be generated on the standalone server;
- Configurable expiration date and time;
- Tokens are compact and easy to transmit.

Available actions are listed [here](doc:authentication#section-available-actions).

TLS connectivity for devices and apps communication is provided.

Access for users, networks and devices is role-based.

Please have a look at the charts which illustrate [HTTPS](doc:https) and [WebSocket](doc:websockets-1) secure connection.

You may also check our [HTTPS configuration guide](doc:https-configuration-ssltls).
