---
title: "Client/Device"
slug: "clientdevice"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 12 2017 19:02:27 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
The service allows clients to exchange messages with the DeviceHive server using a single persistent connection.

After connection is established, clients need to authenticate using JSON Web Token, and then start sending commands to devices using the command/insert message. As soon as a command is processed by a device, the server sends the command/update message.

After connection is established, devices need to register using the device/save message, perform authentication and then start sending notifications using the notification/insert message.

Clients may also subscribe to device notifications using the notification/subscribe message and then start receiving server-originated messages about new device notifications.

Devices may also subscribe to commands using the command/subscrive message and then start receiving server-originated messages about new commands.

## WebSocket Handshake URI

```text
GET /client
GET /device
```

## Messages

| Message                  | Originator    | Authorization                                                     | Description                                                                                                                                                            |
| :----------------------- | :------------ | :---------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| authenticate             | Client/Device | None                                                              | Authenticates a client / device with access JSON Web Token. After successful authentication, all subsequent messages may exclude JSON Web Token parameter.             |
| command/get              | Client/Device | Access JSON Web Token (GetDeviceCommand)                          | Gets information about the command.                                                                                                                                    |
| command/list             | Client/Device | Access JSON Web Token (GetDeviceCommand)                          | Gets the list of commands.                                                                                                                                             |
| command/insert           | Client/Device | Access JSON Web Token (CreateDeviceCommand)                       | Creates new device command.                                                                                                                                            |
| command/subscribe        | Client/Device | Access JSON Web Token (GetDeviceCommand)                          | Subscribes to device commands. After subscription is completed, the server will start to send command/insert messages to the connected user.                           |
| command/unsubscribe      | Client/Device | Access JSON Web Token (GetDeviceCommand)                          | Unsubscribes from device commands.                                                                                                                                     |
| command/update           | Client/Device | Access JSON Web Token (UpdateDeviceCommand)                       | Updates an existing device command on behalf of device.                                                                                                                |
| device/get               | Client/Device | Access JSON Web Token (GetDevice)                                 | Gets information about the current device.                                                                                                                             |
| device/list              | Client/Device | Access JSON Web Token (GetDevice)                                 | Gets information about the current device.                                                                                                                             |
| device/save              | Client/Device | Access JSON Web Token (RegisterDevice)                            | Registers or updates a device.                                                                                                                                         |
| notification/get         | Client/Device | Access JSON Web Token (GetDeviceNotification)                     | Gets information about the notification.                                                                                                                               |
| notification/list        | Client/Device | Access JSON Web Token (GetDeviceNotification)                     | Gets the list of notifications.                                                                                                                                        |
| notification/insert      | Client/Device | Access JSON Web Token (CreateDeviceNotification)                  | Creates new device notification on behalf of device.                                                                                                                   |
| notification/subscribe   | Client/Device | Access JSON Web Token (GetDeviceNotification)                     | Subscribes to device notifications. After subscription is completed, the server will start to send notification/insert messages to the connected user.                 |
| notification/unsubscribe | Client/Device | Access JSON Web Token (GetDeviceNotification)                     | Unsubscribes from device notifications.                                                                                                                                |
| subscription/list        | Client/Device | Access JSON Web Token (GetDeviceCommand or GetDeviceNotification) | Returns list of user subscriptions.                                                                                                                                    |
| server/info              | Client/Device | None                                                              | Gets meta-information about the current API.                                                                                                                           |
| srv: command/insert      | Server        | n/a                                                               | Notifies the user about new device command.                                                                                                                            |
| srv: command/update      | Server        | n/a                                                               | Notifies the user about a command has been processed by a device. These messages are sent only for commands created by the current user within the current connection. |
| srv: notification/insert | Server        | n/a                                                               | Notifies the user about new device notification.                                                                                                                       |
