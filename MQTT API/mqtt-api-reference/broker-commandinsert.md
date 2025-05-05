---
title: "broker: command/update"
slug: "broker-commandinsert"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:03:18 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:57:49 GMT+0000 (Coordinated Universal Time)"
---
Notifies the user about a command has been processed by a device. These messages are sent only for commands created by the current user within the current connection.

## Subscription Topic and Payload

**Topic**

```text
dh/command_update/{network-id}/{devicetype-id}/{device-id}/{command-name}
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
    "command": {
        "id": {integer},
        "timestamp": {datetime},
        "userId": {integer},
        "command": {string},
        "parameters": {object},
        "lifetime": {integer},
        "status": {string},
        "result": {object}
    }
}
```

**Payload Parameters**

| Property Name      | Type     | Description                                                                         |
| :----------------- | :------- | :---------------------------------------------------------------------------------- |
| action             | string   | Action name: command/update                                                         |
| command            | object   | A  [DeviceCommand](doc:devicecommand)  resource representing the processed command. |
| command.id         | integer  | Command identifier.                                                                 |
| command.timestamp  | datetime | Command timestamp (UTC).                                                            |
| command.userId     | integer  | Associated user identifier.                                                         |
| command.command    | string   | Command name.                                                                       |
| command.parameters | object   | Command parameters, a JSON object with an arbitrary structure.                      |
| command.lifetime   | integer  | Command lifetime, a number of seconds until this command expires.                   |
| command.status     | string   | Command status, as reported by device or related infrastructure.                    |
| command.result     | object   | Command execution result, an optional value that could be provided by device.       |
