---
title: "MQTT API Reference"
slug: "mqtt-api-reference"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Feb 07 2018 14:32:45 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:49:29 GMT+0000 (Coordinated Universal Time)"
---
The DeviceHive MQTT API exposes the following services:

## Client (Device)

The service allows clients to exchange messages with the DeviceHive server using a single persistent MQTT connection.

There is an ability to make a connection to the DeviceHive MQTT broker with the user credentials (e.g. username and password) or, after the connection is established, clients are able to authenticate using JSON Web Token, and then start sending commands to devices using the command/insert message or native MQTT publishing mechanism. As soon as a command is processed by a device, the server sends the command/update message.

After connection is established, devices need to register using the device/save message, perform authentication and then start sending notifications using the notification/insert message.

Clients may also subscribe to the device notifications using the native MQTT subscription mechanism and then start receiving server-originated messages about new device notifications.

Devices may also subscribe to commands using the native MQTT subscription mechanism and then start receiving server-originated messages about new commands.

## Native MQTT functionality

- MQTT 3.1 and 3.1.1 compliant.
- QoS 0 and QoS 1.
- Last will functionality

**MQTT Client basic connection options**

| Option | Mandatory | Type | Default |
| --- | --- | --- | --- |
| Host | yes | String | - |
| Port | yes | Number | 1883 |
| Client Id | yes | String | - |
| Keepalive | no | Number | 60 sec |
| Username | no | String | - |
| Password | no | String | - |
| Clean | no | Boolean | false |
| Last will | no | Depends on client realization | - |



Connection options mentioned above a bit depend on the tool that are used to implement MQTT client functionality (e.g. programming language, library, framework...). Please, read the documentation of the tool that you use before configuring MQTT client.

## DeviceHive MQTT topic structure

DeviceHive MQTT Broker gives an ability for clients to communicate with DeviceHive server using MQTT topics in specific format described below. However, in the same time, ordinary MQTT topics also available for clients. Furthermore, clients are able to use them without any authentication.

**Request**

To make a request to the DeviceHive a client should publish a message with specific action field to the **dh/request** topic. List of supported actions is mentioned below (API list part)

Example:

```javascript
mqttClient.publish('dh/request', '{"action":"device/list"}');
```

**Response**

To receive a response a client should subscribe for topic with the next structure:

**dh/response/{request-action}@{client-id}**

Where:

- request-action - action field mentioned in request
- client-id - MQTT client own id

The **@{client-id}** part of the topic is mandatory. It gives an ability to Broker to send response only to request originator

Example: 

```javascript
mqttClient.subscribe('dh/response/device/list@mqttClientId');
```

**Notification/Command publishing**

Notification insert topic template:  
**dh/notification/{network-id}/{devicetype-id}/{device-id}/{notification-name}**

Command insert topic template:  
**dh/command/{network-id}/{devicetype-id}/{device-id}/{command-name}**

Command update topic template:  
**dh/command_update/{network-id}/{devicetype-id}/{device-id}/{command-name}**

Where:

- network-id - DeviceHive Network ID
- devicetype-id - DeviceHive DeviceType ID
- device-id - DeviceHive Device ID
- notification-name - Notification name
- command-name - Command name

Example: 

```javascript
mqttClient.publish('dh/notification/network1/devicetype1/device1/temperature', notificationObject);
mqttClient.publish('dh/command/network1/devicetype1/device1/light', commandObject);
mqttClient.publish('dh/command_update/network1/devicetype1/device1/light', updatedCommandObject);
```

**Notification/Command subscrubtion/unsubscription**

Notification insert subscription topic template:  
**dh/notification/{network-id}/{devicetype-id}/{device-id}/{notification-name}**

Command insert subscription topic template:  
**dh/command/{network-id}/{devicetype-id}/{device-id}/{command-name}**

Command update subscription topic template:  
**dh/command_update/{network-id}/{devicetype-id}/{device-id}/{command-name}**

Where:

- network-id - DeviceHive Network ID
- devicetype-id - DeviceHive DeviceType ID
- device-id - DeviceHive Device ID
- notification-name - Notification name
- command-name - Command name

Example: 

```javascript
client.subscribe('dh/notification/network1/devicetype1/device1/temperature');
    client.subscribe('dh/command/network1/devicetype1/device1/light');
    client.subscribe('dh/command_update/network1/devicetype1/device1/light');
```

**Subscription topic wildcards**

There is an ability to subscribe to the wide range of networks/devicetypes/devices/names

MQTT supports the next wildcards:

- **+** - single level wildcard
- **#** - multi level wildcard

Example:

```javascript
// Global notification subscription
    client.subscribe('dh/notification/#');
    // Subscription for a specific command name on any device on  mentioned network and with specific device type
    client.subscribe('dh/command/network1/devicetype1/+/light');
    // Subscription for command update with any name but with a specific device type on every network and device
    client.subscribe('dh/command_update/+/devicetype1/#');
```

## API list

| Request (Publish) | Response (Subscription) topic | Originator | Authorization |
| --- | --- | --- | --- |
| [**Topic**: dh/request  
**Payload action**: authenticate](doc:authenticate-1) | dh/response/authenticate@<mqtt-client-id> | Client/Device | None |
| [**Topic**: dh/request  
**Payload action**: configuration/get](doc:configurationget-1) | dh/response/configuration/get@<mqtt-client-id> | Client/Device | Access JSON Web Token (ManageConfiguration) |
| [**Topic**: dh/request  
**Payload action**: configuration/put](doc:configurationput-1) | dh/response/configuration/put@<mqtt-client-id> | Client/Device | Access JSON Web Token (ManageConfiguration) |
| [**Topic**: dh/request  
**Payload action**: configuration/delete](doc:configurationdelete-1) | dh/response/configuration/delete@<mqtt-client-id> | Client/Device | Access JSON Web Token (ManageConfiguration) |
| [**Topic**: dh/request  
**Payload action**: command/get](doc:commandget-1) | dh/response/command/get@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDeviceCommand) |
| [**Topic**: dh/request  
**Payload action**: command/list](doc:commandlist-1) | dh/response/command/list@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDeviceCommand) |
| [**Topic**: dh/request  
**Payload action**: command/insert](doc:commandinsert-1) | dh/response/command/insert@<mqtt-client-id> | Client/Device | Access JSON Web Token (CreateDeviceCommand) |
| [**Topic**: dh/request  
**Payload action**: command/subscribe](doc:commandsubscribe-1) | dh/response/command/subscribe@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDeviceCommand) |
| [**Topic**: dh/request  
**Payload action**: command/unsubscribe](doc:commandunsubscribe-1) | dh/response/command/unsubscribe@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDeviceCommand) |
| [**Topic**: dh/request  
**Payload action**: command/update](doc:commandupdate-1) | dh/response/command/update@<mqtt-client-id> | Client/Device | Access JSON Web Token (UpdateDeviceCommand) |
| [**Topic**: dh/request  
**Payload action**: deviceget](doc:) | dh/response/device/get@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDevice) |
| [**Topic**: dh/request  
**Payload action**: device/list](doc:devicelist-1) | dh/response/device/list@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDevice) |
| [**Topic**: dh/request  
**Payload action**: device/count](doc:devicecount-1) | dh/response/device/count@<mqtt-client-id> | Client/Device | Access JSON Web Token (RegisterDevice) |
| [**Topic**: dh/request  
**Payload action**: device/save](doc:devicesave-1) | dh/response/device/save@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDevice) |
| [**Topic**: dh/request  
**Payload action**: device/delete](doc:devicedelete-1) | dh/response/device/delete@<mqtt-client-id> | Client/Device | Access JSON Web Token (RegisterDevice) |
| [**Topic**: dh/request  
**Payload action**: devicetype/list](doc:devicetypelist-1) | dh/response/devicetype/list@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDeviceType) |
| [**Topic**: dh/request  
**Payload action**: devicetype/count](doc:devicetypecount-1) | dh/response/devicetype/count@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDeviceType) |
| [**Topic**: dh/request  
**Payload action**: devicetype/get](doc:devicetypeget-1) | dh/response/devicetype/get@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDeviceType) |
| [**Topic**: dh/request  
**Payload action**: devicetype/insert](doc:devicetypeinsert-1) | dh/response/devicetype/insert@<mqtt-client-id> | Client/Device | Access JSON Web Token (ManageDeviceType) |
| [**Topic**: dh/request  
**Payload action**: devicetype/update](doc:devicetypeupdate-1) | dh/response/devicetype/update@<mqtt-client-id> | Client/Device | Access JSON Web Token (ManageDeviceType) |
| [**Topic**: dh/request  
**Payload action**: devicetype/delete](doc:devicetypedelete-1) | dh/response/devicetype/delete@<mqtt-client-id> | Client/Device | Access JSON Web Token (ManageDeviceType) |
| [**Topic**: dh/request  
**Payload action**: network/list](doc:networklist-1) | dh/response/network/list@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetNetwork) |
| [**Topic**: dh/request  
**Payload action**: network/count](doc:networkcount-1) | dh/response/network/count@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetNetwork) |
| [**Topic**: dh/request  
**Payload action**: network/get](doc:networkget-1) | dh/response/network/get@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetNetwork) |
| [**Topic**: dh/request  
**Payload action**: network/insert](doc:networkinsert-1) | dh/response/network/insert@<mqtt-client-id> | Client/Device | Access JSON Web Token (ManageNetwork) |
| [**Topic**: dh/request  
**Payload action**: network/update](doc:networkupdate-1) | dh/response/network/update@<mqtt-client-id> | Client/Device | Access JSON Web Token (ManageNetwork) |
| [**Topic**: dh/request  
**Payload action**: network/delete](doc:networkdelete-1) | dh/response/network/delete@<mqtt-client-id> | Client/Device | Access JSON Web Token (ManageNetwork) |
| [**Topic**: dh/request  
**Payload action**: user/list](doc:userlist-1) | dh/response/user/list@<mqtt-client-id> | Client/Device | Access JSON Web Token () |
| [**Topic**: dh/request  
**Payload action**: user/count](doc:usercount-1) | dh/response/user/count@<mqtt-client-id> | Client/Device | Access JSON Web Token () |
| [**Topic**: dh/request  
**Payload action**: userget](doc:user/get-1) | dh/response/user/get@<mqtt-client-id> | Client/Device | Access JSON Web Token () |
| [**Topic**: dh/request  
**Payload action**: user/insert](doc:userinsert-1) | dh/response/user/insert@<mqtt-client-id> | Client/Device | Access JSON Web Token () |
| [**Topic**: dh/request  
**Payload action**: user/update](doc:userupdate-1) | dh/response/user/update@<mqtt-client-id> | Client/Device | Access JSON Web Token () |
| [**Topic**: dh/request  
**Payload action**: user/delete](doc:userdelete-1) | dh/response/user/delete@<mqtt-client-id> | Client/Device | Access JSON Web Token () |
| [**Topic**: dh/request  
**Payload action**: user/getCurrent](doc:usergetcurrent-1) | dh/response/user/getCurrent@<mqtt-client-id> | Client/Device | Access JSON Web Token () |
| [**Topic**: dh/request  
**Payload action**: user/updateCurrent](doc:userupdatecurrent-1) | dh/response/user/updateCurrent@<mqtt-client-id> | Client/Device | Access JSON Web Token () |
| [**Topic**: dh/request  
**Payload action**: user/getNetwork](doc:usergetnetwork-1) | dh/response/user/getNetwork@<mqtt-client-id> | Client/Device | Access JSON Web Token () |
| [**Topic**: dh/request  
**Payload action**: user/assignNetwork](doc:userassignnetwork-1) | dh/response/user/assignNetwork@<mqtt-client-id> | Client/Device | Access JSON Web Token () |
| [**Topic**: dh/request  
**Payload action**: user/unassignNetwork](doc:userunassignnetwork-1) | dh/response/user/unassignNetwork@<mqtt-client-id> | Client/Device | Access JSON Web Token () |
| [**Topic**: dh/request  
**Payload action**: notification/get](doc:notificationget-1) | dh/response/notification/get@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDeviceNotification) |
| [**Topic**: dh/request  
**Payload action**: notification/list](doc:notificationlist-1) | dh/response/notification/list@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDeviceNotification) |
| [**Topic**: dh/request  
**Payload action**: notification/insert](doc:notificationinsert-1) | dh/response/notification/insert@<mqtt-client-id> | Client/Device | Access JSON Web Token (CreateDeviceNotification) |
| [**Topic**: dh/request  
**Payload action**: notification/subscribe](doc:notificationsubscribe-1) | dh/response/notification/subscribe@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDeviceNotification) |
| [**Topic**: dh/request  
**Payload action**: notification/unsubscribe](doc:notificationunsubscribe-1) | dh/response/notification/unsubscribe@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDeviceNotification) |
| [**Topic**: dh/request  
**Payload action**: subscription/list](doc:subscriptionlist-1) | dh/response/subscription/list@<mqtt-client-id> | Client/Device | Access JSON Web Token (GetDeviceCommand or GetDeviceNotification) |
| [**Topic**: dh/request  
**Payload action**: server/info](doc:serverinfo-1) | dh/response/server/info@<mqtt-client-id> | Client/Device | None |
| [**Topic**: dh/request  
**Payload action**: token](doc:token-1) | dh/response/token@<mqtt-client-id> | Client/Device | None |
| [**Topic**: dh/request  
**Payload action**: token/create](doc:tokencreate-1) | dh/response/token/create@<mqtt-client-id> | Client/Device | Access JSON Web Token (ManageToken) |
| [**Topic**: dh/request  
**Payload action**: token/refresh](doc:tokenrefresh-1) | dh/response/token/refresh@<mqtt-client-id> | Client/Device | None |
| [broker: command/insert](doc:broker-commandinsert) | dh/command/{network-id}/{device-type-id}/{device-id}/{command-name} | Broker | n/a |
| [broker: command/update](doc:broker-commandupdate) | dh/command_update/{network-id}/{device-type-id}/{device-id}/{command-name} | Broker | n/a |
| [broker: notification/insert](doc:broker-notificationinsert) | dh/notification/{network-id}/{device-type-id}/{device-id}/{command-name} | Broker | n/a |



More information on GitHub:  
[DeviceHive MQTT Broker](https://github.com/devicehive/devicehive-mqtt)

