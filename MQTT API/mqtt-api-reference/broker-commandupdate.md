---
title: "broker: command/insert"
slug: "broker-commandupdate"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:03:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:57:35 GMT+0000 (Coordinated Universal Time)"
---
Notifies the user about new device command.

## Subscription Topic and Payload

**Topic**

```text
dh/command/{network-id}/{devicetype-id}/{device-id}/{command-name}
```

Where:

- network-id - DeviceHive Network ID
- devicetype-id - DeviceHive DeviceType ID
- device-id - DeviceHive Device ID
- command-name - Command name

**Payload Representation**

```text
{
    "action": {string},
    "subscriptionId": {guid},
    "command": {
        "id": {integer},
        "timestamp": {datetime},
        "userId": {integer},
        "deviceId": {string},
        "command": {string},
        "parameters": {object},
        "lifetime": {integer},
        "status": {string},
        "result": {object}
    }
}
```

**Payload Parameters**

| Property Name      | Type     | Description                                                                   |
| :----------------- | :------- | :---------------------------------------------------------------------------- |
| action             | string   | Action name: command/insert                                                   |
| subscriptionId     | guid     | Identifier of the associated subscription.                                    |
| command            | object   | A [DeviceCommand](doc:devicecommand)  resource representing the command.      |
| command.id         | integer  | Command identifier.                                                           |
| command.timestamp  | datetime | Command timestamp (UTC).                                                      |
| command.userId     | integer  | Associated user identifier.                                                   |
| command.deviceId   | string   | Device unique identifier.                                                     |
| command.command    | string   | Command name.                                                                 |
| command.parameters | object   | Command parameters, a JSON object with an arbitrary structure.                |
| command.lifetime   | integer  | Command lifetime, a number of seconds until this command expires.             |
| command.status     | string   | Command status, as reported by device or related infrastructure.              |
| command.result     | object   | Command execution result, an optional value that could be provided by device. |
