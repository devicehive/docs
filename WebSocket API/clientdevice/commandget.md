---
title: "command/get"
slug: "commandget"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 12 2017 19:19:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Apr 12 2018 09:58:31 GMT+0000 (Coordinated Universal Time)"
---
Gets information about the command.

## Request Message

**Authorization**

Access JSON Web Token (GetDeviceCommand)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string},
    "commandId": {long}
}
```

**Message Parameters**

| Property Name | Required | Type   | Descripton                                                              |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: command/get                                                |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| deviceId      | Yes      | string | Device unique identifier.                                               |
| commandId     | Yes      | long   | Command unique identifier.                                              |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "command": {
        "id": {long},
        "command": {string},
        "timestamp": {datetime},
        "lastUpdated": {datetime},
        "userId": {integer},
        "deviceId": {string},
        "networkId": {integer},
        "parameters": {object},
        "lifetime": {integer},
        "status": {string},
        "result": {object}
    }
}
```

**Message Parameters**

| Property Name       | Type     | Description                                                                                                      |
| :------------------ | :------- | :--------------------------------------------------------------------------------------------------------------- |
| action              | string   | Action name: command/get                                                                                         |
| status              | string   | Operation execution status (success or error).                                                                   |
| requestId           | object   | Request unique identifier as specified in the request message.                                                   |
| command             | object   | An inserted [DeviceCommand](doc:devicecommand)  resource.                                                        |
| command.id          | long     | Command identifier.                                                                                              |
| command.command     | string   | Command name.                                                                                                    |
| command.timestamp   | datetime | Command UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)).             |
| command.lastUpdated | datetime | Last command update UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| command.userId      | integer  | Associated user identifier.                                                                                      |
| command.deviceId    | string   | Associated device identifier.                                                                                    |
| command.networkId   | integer  | Associated network identifier.                                                                                   |
| command.parameters  | object   | Command parameters, a JSON object with an arbitrary structure.                                                   |
| command.lifetime    | integer  | Command lifetime, a number of seconds until this command expires.                                                |
| command.status      | string   | Command status, as reported by device or related infrastructure.                                                 |
| command.result      | object   | Command execution result, an optional value that could be provided by device.                                    |
