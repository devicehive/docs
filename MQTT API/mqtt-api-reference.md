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

[block:parameters]
{
  "data": {
    "h-0": "Option",
    "h-1": "Mandatory",
    "h-2": "Type",
    "h-3": "Default",
    "h-4": "Description",
    "0-0": "Host",
    "0-1": "yes",
    "0-2": "String",
    "0-3": "-",
    "0-4": "DeviceHive MQTT Broker host address",
    "1-0": "Port",
    "1-1": "yes",
    "1-2": "Number",
    "1-3": "1883",
    "1-4": "DeviceHive  MQTT Broker port",
    "2-0": "Client Id",
    "2-1": "yes",
    "2-2": "String",
    "2-3": "-",
    "2-4": "Client (Device) identificator.",
    "3-0": "Keepalive",
    "3-1": "no",
    "3-2": "Number",
    "3-3": "60 sec",
    "3-4": "The keep alive functionality assures that the connection is still open and both broker and client are connected to one another.  \nSet to 0 to disable",
    "4-0": "Username",
    "4-1": "no",
    "4-2": "String",
    "4-3": "-",
    "4-4": "DeviceHive user's login",
    "5-0": "Password",
    "5-1": "no",
    "5-2": "String",
    "5-3": "-",
    "5-4": "DeviceHive user's password",
    "6-0": "Clean",
    "6-1": "no",
    "6-2": "Boolean",
    "6-3": "false",
    "6-4": "Set to false to receive QoS 1 and 2 messages while offline",
    "7-0": "Last will",
    "7-1": "no",
    "7-2": "Depends on client realization",
    "7-3": "-",
    "7-4": "A message that will sent by the broker automatically when the client disconnect badly"
  },
  "cols": 5,
  "rows": 8,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


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

[block:parameters]
{
  "data": {
    "h-0": "Request (Publish)",
    "h-1": "Response (Subscription) topic",
    "h-2": "Originator",
    "h-3": "Authorization",
    "h-4": "Description",
    "0-0": "[**Topic**: dh/request  \n**Payload action**: authenticate](doc:authenticate-1)",
    "0-1": "dh/response/authenticate@<mqtt-client-id>",
    "0-2": "Client/Device",
    "0-3": "None",
    "0-4": "Authenticates a client by a JSON Web Token.",
    "1-0": "[**Topic**: dh/request  \n**Payload action**: configuration/get](doc:configurationget-1)",
    "1-1": "dh/response/configuration/get@<mqtt-client-id>",
    "1-2": "Client/Device",
    "1-3": "Access JSON Web Token (ManageConfiguration)",
    "1-4": "Returns requested property value.",
    "2-0": "[**Topic**: dh/request  \n**Payload action**: configuration/put](doc:configurationput-1)",
    "2-1": "dh/response/configuration/put@<mqtt-client-id>",
    "2-2": "Client/Device",
    "2-3": "Access JSON Web Token (ManageConfiguration)",
    "2-4": "Creates new or updates existing property.",
    "3-0": "[**Topic**: dh/request  \n**Payload action**: configuration/delete](doc:configurationdelete-1)",
    "3-1": "dh/response/configuration/delete@<mqtt-client-id>",
    "3-2": "Client/Device",
    "3-3": "Access JSON Web Token (ManageConfiguration)",
    "3-4": "Deletes a property.",
    "4-0": "[**Topic**: dh/request  \n**Payload action**: command/get](doc:commandget-1)",
    "4-1": "dh/response/command/get@<mqtt-client-id>",
    "4-2": "Client/Device",
    "4-3": "Access JSON Web Token (GetDeviceCommand)",
    "4-4": "Gets information about the command.",
    "5-0": "[**Topic**: dh/request  \n**Payload action**: command/list](doc:commandlist-1)",
    "5-1": "dh/response/command/list@<mqtt-client-id>",
    "5-2": "Client/Device",
    "5-3": "Access JSON Web Token (GetDeviceCommand)",
    "5-4": "Gets the list of commands.",
    "6-0": "[**Topic**: dh/request  \n**Payload action**: command/insert](doc:commandinsert-1)",
    "6-1": "dh/response/command/insert@<mqtt-client-id>",
    "6-2": "Client/Device",
    "6-3": "Access JSON Web Token (CreateDeviceCommand)",
    "6-4": "Creates new device command.",
    "7-0": "[**Topic**: dh/request  \n**Payload action**: command/subscribe](doc:commandsubscribe-1)",
    "7-1": "dh/response/command/subscribe@<mqtt-client-id>",
    "7-2": "Client/Device",
    "7-3": "Access JSON Web Token (GetDeviceCommand)",
    "7-4": "Subscribes to device commands. After subscription is completed, the server will start to send command/insert messages to the connected user.",
    "8-0": "[**Topic**: dh/request  \n**Payload action**: command/unsubscribe](doc:commandunsubscribe-1)",
    "8-1": "dh/response/command/unsubscribe@<mqtt-client-id>",
    "8-2": "Client/Device",
    "8-3": "Access JSON Web Token (GetDeviceCommand)",
    "8-4": "Unsubscribes from device commands.",
    "9-0": "[**Topic**: dh/request  \n**Payload action**: command/update](doc:commandupdate-1)",
    "9-1": "dh/response/command/update@<mqtt-client-id>",
    "9-2": "Client/Device",
    "9-3": "Access JSON Web Token (UpdateDeviceCommand)",
    "9-4": "Updates an existing device command on behalf of device.",
    "10-0": "[**Topic**: dh/request  \n**Payload action**: deviceget](doc:)",
    "10-1": "dh/response/device/get@<mqtt-client-id>",
    "10-2": "Client/Device",
    "10-3": "Access JSON Web Token (GetDevice)",
    "10-4": "Gets information about the current device.",
    "11-0": "[**Topic**: dh/request  \n**Payload action**: device/list](doc:devicelist-1)",
    "11-1": "dh/response/device/list@<mqtt-client-id>",
    "11-2": "Client/Device",
    "11-3": "Access JSON Web Token (GetDevice)",
    "11-4": "Gets the list of devices.",
    "12-0": "[**Topic**: dh/request  \n**Payload action**: device/count](doc:devicecount-1)",
    "12-1": "dh/response/device/count@<mqtt-client-id>",
    "12-2": "Client/Device",
    "12-3": "Access JSON Web Token (RegisterDevice)",
    "12-4": "Gets count of devices.",
    "13-0": "[**Topic**: dh/request  \n**Payload action**: device/save](doc:devicesave-1)",
    "13-1": "dh/response/device/save@<mqtt-client-id>",
    "13-2": "Client/Device",
    "13-3": "Access JSON Web Token (GetDevice)",
    "13-4": "Registers or updates a device.",
    "14-0": "[**Topic**: dh/request  \n**Payload action**: device/delete](doc:devicedelete-1)",
    "14-1": "dh/response/device/delete@<mqtt-client-id>",
    "14-2": "Client/Device",
    "14-3": "Access JSON Web Token (RegisterDevice)",
    "14-4": "Deletes a device.",
    "15-0": "[**Topic**: dh/request  \n**Payload action**: devicetype/list](doc:devicetypelist-1)",
    "15-1": "dh/response/devicetype/list@<mqtt-client-id>",
    "15-2": "Client/Device",
    "15-3": "Access JSON Web Token (GetDeviceType)",
    "15-4": "Gets list of device types. The result list is limited to device types the client has access to.",
    "16-0": "[**Topic**: dh/request  \n**Payload action**: devicetype/count](doc:devicetypecount-1)",
    "16-1": "dh/response/devicetype/count@<mqtt-client-id>",
    "16-2": "Client/Device",
    "16-3": "Access JSON Web Token (GetDeviceType)",
    "16-4": "Gets count of device types the client has access to.",
    "17-0": "[**Topic**: dh/request  \n**Payload action**: devicetype/get](doc:devicetypeget-1)",
    "17-1": "dh/response/devicetype/get@<mqtt-client-id>",
    "17-2": "Client/Device",
    "17-3": "Access JSON Web Token (GetDeviceType)",
    "17-4": "Gets information about device type and its devices.",
    "18-0": "[**Topic**: dh/request  \n**Payload action**: devicetype/insert](doc:devicetypeinsert-1)",
    "18-1": "dh/response/devicetype/insert@<mqtt-client-id>",
    "18-2": "Client/Device",
    "18-3": "Access JSON Web Token (ManageDeviceType)",
    "18-4": "Creates new device type.",
    "19-0": "[**Topic**: dh/request  \n**Payload action**: devicetype/update](doc:devicetypeupdate-1)",
    "19-1": "dh/response/devicetype/update@<mqtt-client-id>",
    "19-2": "Client/Device",
    "19-3": "Access JSON Web Token (ManageDeviceType)",
    "19-4": "Updates an existing device type.",
    "20-0": "[**Topic**: dh/request  \n**Payload action**: devicetype/delete](doc:devicetypedelete-1)",
    "20-1": "dh/response/devicetype/delete@<mqtt-client-id>",
    "20-2": "Client/Device",
    "20-3": "Access JSON Web Token (ManageDeviceType)",
    "20-4": "Deletes an existing device type.",
    "21-0": "[**Topic**: dh/request  \n**Payload action**: network/list](doc:networklist-1)",
    "21-1": "dh/response/network/list@<mqtt-client-id>",
    "21-2": "Client/Device",
    "21-3": "Access JSON Web Token (GetNetwork)",
    "21-4": "Gets the list of networks.",
    "22-0": "[**Topic**: dh/request  \n**Payload action**: network/count](doc:networkcount-1)",
    "22-1": "dh/response/network/count@<mqtt-client-id>",
    "22-2": "Client/Device",
    "22-3": "Access JSON Web Token (GetNetwork)",
    "22-4": "Gets count of networks.",
    "23-0": "[**Topic**: dh/request  \n**Payload action**: network/get](doc:networkget-1)",
    "23-1": "dh/response/network/get@<mqtt-client-id>",
    "23-2": "Client/Device",
    "23-3": "Access JSON Web Token (GetNetwork)",
    "23-4": "Gets a network by ID.",
    "24-0": "[**Topic**: dh/request  \n**Payload action**: network/insert](doc:networkinsert-1)",
    "24-1": "dh/response/network/insert@<mqtt-client-id>",
    "24-2": "Client/Device",
    "24-3": "Access JSON Web Token (ManageNetwork)",
    "24-4": "Inserts new network.",
    "25-0": "[**Topic**: dh/request  \n**Payload action**: network/update](doc:networkupdate-1)",
    "25-1": "dh/response/network/update@<mqtt-client-id>",
    "25-2": "Client/Device",
    "25-3": "Access JSON Web Token (ManageNetwork)",
    "25-4": "Updates a network.",
    "26-0": "[**Topic**: dh/request  \n**Payload action**: network/delete](doc:networkdelete-1)",
    "26-1": "dh/response/network/delete@<mqtt-client-id>",
    "26-2": "Client/Device",
    "26-3": "Access JSON Web Token (ManageNetwork)",
    "26-4": "Deletes a network by ID.",
    "27-0": "[**Topic**: dh/request  \n**Payload action**: user/list](doc:userlist-1)",
    "27-1": "dh/response/user/list@<mqtt-client-id>",
    "27-2": "Client/Device",
    "27-3": "Access JSON Web Token ()",
    "27-4": "Gets list of users.",
    "28-0": "[**Topic**: dh/request  \n**Payload action**: user/count](doc:usercount-1)",
    "28-1": "dh/response/user/count@<mqtt-client-id>",
    "28-2": "Client/Device",
    "28-3": "Access JSON Web Token ()",
    "28-4": "Gets count of users.",
    "29-0": "[**Topic**: dh/request  \n**Payload action**: userget](doc:user/get-1)",
    "29-1": "dh/response/user/get@<mqtt-client-id>",
    "29-2": "Client/Device",
    "29-3": "Access JSON Web Token ()",
    "29-4": "Gets information about user and its assigned networks.",
    "30-0": "[**Topic**: dh/request  \n**Payload action**: user/insert](doc:userinsert-1)",
    "30-1": "dh/response/user/insert@<mqtt-client-id>",
    "30-2": "Client/Device",
    "30-3": "Access JSON Web Token ()",
    "30-4": "Creates new user",
    "31-0": "[**Topic**: dh/request  \n**Payload action**: user/update](doc:userupdate-1)",
    "31-1": "dh/response/user/update@<mqtt-client-id>",
    "31-2": "Client/Device",
    "31-3": "Access JSON Web Token ()",
    "31-4": "Updates an existing user.",
    "32-0": "[**Topic**: dh/request  \n**Payload action**: user/delete](doc:userdelete-1)",
    "32-1": "dh/response/user/delete@<mqtt-client-id>",
    "32-2": "Client/Device",
    "32-3": "Access JSON Web Token ()",
    "32-4": "Deletes an existing user.",
    "33-0": "[**Topic**: dh/request  \n**Payload action**: user/getCurrent](doc:usergetcurrent-1)",
    "33-1": "dh/response/user/getCurrent@<mqtt-client-id>",
    "33-2": "Client/Device",
    "33-3": "Access JSON Web Token ()",
    "33-4": "Gets information about user and its assigned networks.",
    "34-0": "[**Topic**: dh/request  \n**Payload action**: user/updateCurrent](doc:userupdatecurrent-1)",
    "34-1": "dh/response/user/updateCurrent@<mqtt-client-id>",
    "34-2": "Client/Device",
    "34-3": "Access JSON Web Token ()",
    "34-4": "Updates an existing user.",
    "35-0": "[**Topic**: dh/request  \n**Payload action**: user/getNetwork](doc:usergetnetwork-1)",
    "35-1": "dh/response/user/getNetwork@<mqtt-client-id>",
    "35-2": "Client/Device",
    "35-3": "Access JSON Web Token ()",
    "35-4": "Gets information about user/network association.",
    "36-0": "[**Topic**: dh/request  \n**Payload action**: user/assignNetwork](doc:userassignnetwork-1)",
    "36-1": "dh/response/user/assignNetwork@<mqtt-client-id>",
    "36-2": "Client/Device",
    "36-3": "Access JSON Web Token ()",
    "36-4": "Associates network with the user.",
    "37-0": "[**Topic**: dh/request  \n**Payload action**: user/unassignNetwork](doc:userunassignnetwork-1)",
    "37-1": "dh/response/user/unassignNetwork@<mqtt-client-id>",
    "37-2": "Client/Device",
    "37-3": "Access JSON Web Token ()",
    "37-4": "Removes association between network and user.",
    "38-0": "[**Topic**: dh/request  \n**Payload action**: notification/get](doc:notificationget-1)",
    "38-1": "dh/response/notification/get@<mqtt-client-id>",
    "38-2": "Client/Device",
    "38-3": "Access JSON Web Token (GetDeviceNotification)",
    "38-4": "Gets information about the notification.",
    "39-0": "[**Topic**: dh/request  \n**Payload action**: notification/list](doc:notificationlist-1)",
    "39-1": "dh/response/notification/list@<mqtt-client-id>",
    "39-2": "Client/Device",
    "39-3": "Access JSON Web Token (GetDeviceNotification)",
    "39-4": "Gets the list of notifications.",
    "40-0": "[**Topic**: dh/request  \n**Payload action**: notification/insert](doc:notificationinsert-1)",
    "40-1": "dh/response/notification/insert@<mqtt-client-id>",
    "40-2": "Client/Device",
    "40-3": "Access JSON Web Token (CreateDeviceNotification)",
    "40-4": "Creates new device notification on behalf of device.",
    "41-0": "[**Topic**: dh/request  \n**Payload action**: notification/subscribe](doc:notificationsubscribe-1)",
    "41-1": "dh/response/notification/subscribe@<mqtt-client-id>",
    "41-2": "Client/Device",
    "41-3": "Access JSON Web Token (GetDeviceNotification)",
    "41-4": "Subscribes to device notifications. After subscription is completed, the server will start to send notification/insert messages to the connected user.",
    "42-0": "[**Topic**: dh/request  \n**Payload action**: notification/unsubscribe](doc:notificationunsubscribe-1)",
    "42-1": "dh/response/notification/unsubscribe@<mqtt-client-id>",
    "42-2": "Client/Device",
    "42-3": "Access JSON Web Token (GetDeviceNotification)",
    "42-4": "Unsubscribes from device notifications.",
    "43-0": "[**Topic**: dh/request  \n**Payload action**: subscription/list](doc:subscriptionlist-1)",
    "43-1": "dh/response/subscription/list@<mqtt-client-id>",
    "43-2": "Client/Device",
    "43-3": "Access JSON Web Token (GetDeviceCommand or GetDeviceNotification)",
    "43-4": "Returns list of user subscriptions.",
    "44-0": "[**Topic**: dh/request  \n**Payload action**: server/info](doc:serverinfo-1)",
    "44-1": "dh/response/server/info@<mqtt-client-id>",
    "44-2": "Client/Device",
    "44-3": "None",
    "44-4": "Gets meta-information about the current API.",
    "45-0": "[**Topic**: dh/request  \n**Payload action**: token](doc:token-1)",
    "45-1": "dh/response/token@<mqtt-client-id>",
    "45-2": "Client/Device",
    "45-3": "None",
    "45-4": "Creates access and refresh tokens by login and password.",
    "46-0": "[**Topic**: dh/request  \n**Payload action**: token/create](doc:tokencreate-1)",
    "46-1": "dh/response/token/create@<mqtt-client-id>",
    "46-2": "Client/Device",
    "46-3": "Access JSON Web Token (ManageToken)",
    "46-4": "Creates access and refresh tokens by payload.",
    "47-0": "[**Topic**: dh/request  \n**Payload action**: token/refresh](doc:tokenrefresh-1)",
    "47-1": "dh/response/token/refresh@<mqtt-client-id>",
    "47-2": "Client/Device",
    "47-3": "None",
    "47-4": "Refreshes access token by refresh token.",
    "48-0": "[broker: command/insert](doc:broker-commandinsert)",
    "48-1": "dh/command/{network-id}/{device-type-id}/{device-id}/{command-name}",
    "48-2": "Broker",
    "48-3": "n/a",
    "48-4": "Notifies the user about new device command.",
    "49-0": "[broker: command/update](doc:broker-commandupdate)",
    "49-1": "dh/command_update/{network-id}/{device-type-id}/{device-id}/{command-name}",
    "49-2": "Broker",
    "49-3": "n/a",
    "49-4": "Notifies the user about a command has been processed by a device. These messages are sent only for commands created by the current user within the current connection.",
    "50-0": "[broker: notification/insert](doc:broker-notificationinsert)",
    "50-1": "dh/notification/{network-id}/{device-type-id}/{device-id}/{command-name}",
    "50-2": "Broker",
    "50-3": "n/a",
    "50-4": "Notifies the user about new device notification."
  },
  "cols": 5,
  "rows": 51,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


More information on GitHub:  
[DeviceHive MQTT Broker](https://github.com/devicehive/devicehive-mqtt)
