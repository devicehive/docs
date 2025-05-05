---
title: "WebSocket API Reference"
slug: "websocket-api-reference"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jul 07 2017 08:39:54 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jun 22 2022 14:00:11 GMT+0000 (Coordinated Universal Time)"
---
The DeviceHive WebSocket API exposes the following services:

## Client

The service allows clients to exchange messages with the DeviceHive server using a single persistent connection.

After connection is established, clients need to authenticate using JSON Web Token, and then start sending commands to devices using the command/insert message. As soon as a command is processed by a device, the server sends the command/update message.

After connection is established, devices need to register using the device/save message, perform authentication and then start sending notifications using the notification/insert message.

Clients may also subscribe to device notifications using the notification/subscribe message and then start receiving server-originated messages about new device notifications.

Devices may also subscribe to commands using the command/subscribe message and then start receiving server-originated messages about new commands.

**WebSocket Handshake URI**

```text
GET /client
```

```text
GET /device
```

## Messages

| Message                                                 | Originator    | Authorization                                                     | Description                                                                                                                                                            |
| :------------------------------------------------------ | :------------ | :---------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [authenticate](doc:authenticate)                        | Client/Device | None                                                              | Authenticates a client by a JSON Web Token.                                                                                                                            |
| [configuration/get](doc:configurationget)               | Client/Device | Access JSON Web Token (ManageConfiguration)                       | Returns requested property value.                                                                                                                                      |
| [configuration/put](doc:configurationput)               | Client/Device | Access JSON Web Token (ManageConfiguration)                       | Creates new or updates existing property.                                                                                                                              |
| [configuration/delete](doc:configurationdelete)         | Client/Device | Access JSON Web Token (ManageConfiguration)                       | Deletes a property.                                                                                                                                                    |
| [command/get](doc:commandget)                           | Client/Device | Access JSON Web Token (GetDeviceCommand)                          | Gets information about the command.                                                                                                                                    |
| [command/list](doc:commandlist)                         | Client/Device | Access JSON Web Token (GetDeviceCommand)                          | Gets the list of commands.                                                                                                                                             |
| [command/insert](doc:commandinsert)                     | Client/Device | Access JSON Web Token (CreateDeviceCommand)                       | Creates new device command.                                                                                                                                            |
| [command/subscribe](doc:commandsubscibe)                | Client/Device | Access JSON Web Token (GetDeviceCommand)                          | Subscribes to device commands. After subscription is completed, the server will start to send command/insert messages to the connected user.                           |
| [command/unsubscribe](doc:commandunsubscribe)           | Client/Device | Access JSON Web Token (GetDeviceCommand)                          | Unsubscribes from device commands.                                                                                                                                     |
| [command/update](doc:commandupdate)                     | Client/Device | Access JSON Web Token (UpdateDeviceCommand)                       | Updates an existing device command on behalf of device.                                                                                                                |
| [device/get](doc:deviceget)                             | Client/Device | Access JSON Web Token (GetDevice)                                 | Gets information about the current device.                                                                                                                             |
| [device/list](doc:devicelist)                           | Client/Device | Access JSON Web Token (GetDevice)                                 | Gets the list of devices.                                                                                                                                              |
| [device/save](doc:devicesave)                           | Client/Device | Access JSON Web Token (RegisterDevice)                            | Registers or updates a device.                                                                                                                                         |
| [device/delete](doc:devicedelete)                       | Client/Device | Access JSON Web Token (RegisterDevice)                            | Deletes a device.                                                                                                                                                      |
| [devicetype/list](doc:devicetypelist)                   | Client/Device | Access JSON Web Token (GetDeviceType)                             | Gets list of device types. The result list is limited to device types the client has access to.                                                                        |
| [devicetype/count](doc:devicetypecount)                 | Client/Device | Access JSON Web Token (GetDeviceType)                             | Gets count of device types the client has access to.                                                                                                                   |
| [devicetype/get](doc:devicetypeget)                     | Client/Device | Access JSON Web Token (GetDeviceType)                             | Gets information about device type and its devices.                                                                                                                    |
| [devicetype/insert](doc:devicetypeinsert)               | Client/Device | Access JSON Web Token (ManageDeviceType)                          | Creates new device type.                                                                                                                                               |
| [devicetype/update](doc:devicetypeupdate)               | Client/Device | Access JSON Web Token (ManageDeviceType)                          | Updates an existing device type.                                                                                                                                       |
| [devicetype/delete](doc:devicetypedelete)               | Client/Device | Access JSON Web Token (ManageDeviceType)                          | Deletes an existing device type.                                                                                                                                       |
| [network/list](doc:networklist)                         | Client/Device | Access JSON Web Token (GetNetwork)                                | Gets the list of networks.                                                                                                                                             |
| [network/get](doc:networkget)                           | Client/Device | Access JSON Web Token (GetNetwork)                                | Gets a network by ID.                                                                                                                                                  |
| [network/insert](doc:networkinsert)                     | Client/Device | Access JSON Web Token (ManageNetwork)                             | Inserts new network.                                                                                                                                                   |
| [network/update](doc:networkupdate)                     | Client/Device | Access JSON Web Token (ManageNetwork)                             | Updates a network.                                                                                                                                                     |
| [network/delete](doc:networkdelete)                     | Client/Device | Access JSON Web Token (ManageNetwork)                             | Deletes a network by ID.                                                                                                                                               |
| [notification/get](doc:notificationget)                 | Client/Device | Access JSON Web Token (GetDeviceNotification)                     | Gets information about the notification.                                                                                                                               |
| [notification/list](doc:notificationlist)               | Client/Device | Access JSON Web Token (GetDeviceNotification)                     | Gets the list of notifications.                                                                                                                                        |
| [notification/insert](doc:notificationinsert)           | Client/Device | Access JSON Web Token (CreateDeviceNotification)                  | Creates new device notification on behalf of device.                                                                                                                   |
| [notification/subscribe](doc:notificationsubscribe)     | Client/Device | Access JSON Web Token (GetDeviceNotification)                     | Subscribes to device notifications. After subscription is completed, the server will start to send notification/insert messages to the connected user.                 |
| [notification/unsubscribe](doc:notificationunsubscribe) | Client/Device | Access JSON Web Token (GetDeviceNotification)                     | Unsubscribes from device notifications.                                                                                                                                |
| [subscription/list](doc:subscriptionlist)               | Client/Device | Access JSON Web Token (GetDeviceCommand or GetDeviceNotification) | Returns list of user subscriptions.                                                                                                                                    |
| [server/info](doc:serverinfo)                           | Client/Device | None                                                              | Gets meta-information about the current API.                                                                                                                           |
| [token](doc:token)                                      | Client/Device | None                                                              | Creates access and refresh tokens by login and password.                                                                                                               |
| [token/create](doc:tokencreate)                         | Client/Device | Access JSON Web Token (ManageToken)                               | Creates access and refresh tokens by payload.                                                                                                                          |
| [token/refresh](doc:tokenrefresh)                       | Client/Device | None                                                              | Refreshes access token by refresh token.                                                                                                                               |
| [srv: command/insert](doc:srv-commandinsert)            | Server        | n/a                                                               | Notifies the user about new device command.                                                                                                                            |
| [srv: command/update](doc:srv-commandupdate)            | Server        | n/a                                                               | Notifies the user about a command has been processed by a device. These messages are sent only for commands created by the current user within the current connection. |
| [srv: notification/insert](doc:srv-notificationinsert)  | Server        | n/a                                                               | Notifies the user about new device notification.                                                                                                                       |
