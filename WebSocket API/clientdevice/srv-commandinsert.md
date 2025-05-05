---
title: "srv: command/insert"
slug: "srv-commandinsert"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Sat Jul 15 2017 13:16:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Notifies the user about new device command.

## Server Message

**Message Representation**

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

**Message Parameters**

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
