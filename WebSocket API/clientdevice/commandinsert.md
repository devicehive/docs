---
title: "command/insert"
slug: "commandinsert"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 12 2017 19:19:34 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 23:25:03 GMT+0000 (Coordinated Universal Time)"
---
Creates new device command.

## Request Message

**Authorization**

Access JSON Web Token (CreateDeviceCommand)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string},
    "command": {
        "command": {string},
        "timestamp": {datatime},
        "parameters": {object},
        "lifetime": {integer},
        "status": {string},
        "result": {object}
    }
}
```

**Message Parameters**

| Property Name      | Required | Type     | Description                                                                                          |
| :----------------- | :------- | :------- | :--------------------------------------------------------------------------------------------------- |
| action             | Yes      | string   | Action name: command/insert                                                                          |
| requestId          | No       | object   | Request unique identifier, will be passed back in the response message.                              |
| deviceId           | Yes      | string   | Target device unique identifier.                                                                     |
| command            | Yes      | object   | A DeviceCommand resource to create.                                                                  |
| command.command    | Yes      | string   | Command name.                                                                                        |
| command.timestamp  | No       | datetime | Command UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| command.parameters | No       | object   | Command parameters, a JSON object with an arbitrary structure.                                       |
| command.lifetime   | No       | integer  | Command lifetime, a number of seconds until this command expires.                                    |
| command.status     | No       | string   | Command status, as reported by device or related infrastructure.                                     |
| command.result     | No       | object   | Command execution result, an optional value that could be provided by device.                        |

## Response Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "command": {
        "id": {integer},
        "timestamp": {datetime},
        "lastUpdated": {datetime},
        "userId": {integer}
    }
}
```

**Message Parameters**

| Property Name       | Type     | Description                                                                                                      |
| :------------------ | :------- | :--------------------------------------------------------------------------------------------------------------- |
| action              | string   | Action name: command/insert                                                                                      |
| status              | string   | Operation execution status (success or error).                                                                   |
| requestId           | object   | Request unique identifier as specified in the request message.                                                   |
| command             | object   | An inserted [DeviceCommand](doc:devicecommand)   resource.                                                       |
| command.id          | integer  | Command identifier.                                                                                              |
| command.timestamp   | datetime | Command UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)).             |
| command.lastUpdated | datetime | Last command update UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| command.userId      | integer  | Associated user identifier.                                                                                      |
