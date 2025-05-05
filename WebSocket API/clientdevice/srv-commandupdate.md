---
title: "srv: command/update"
slug: "srv-commandupdate"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Sat Jul 15 2017 13:16:26 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Notifies the user about a command has been processed by a device. These messages are sent only for commands created by the current user within the current connection.

## Server Message

**Message Representation**

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

**Message Parameters**

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
