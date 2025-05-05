---
title: "command/update"
slug: "commandupdate-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:54:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:26:30 GMT+0000 (Coordinated Universal Time)"
---
Updates an existing device command on behalf of device.

**Authorization**

Access JSON Web Token (UpdateDeviceCommand)

## Request Topic and Payload

**Topic**

```text
dh/request
```

**Payload Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string},
    "commandId": {integer},
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

**Payload Parameters**

| Property Name      | Required | Type     | Description                                                                                          |
| :----------------- | :------- | :------- | :--------------------------------------------------------------------------------------------------- |
| action             | Yes      | string   | Action name: command/update                                                                          |
| requestId          | No       | object   | Request unique identifier, will be passed back in the response message.                              |
| deviceId           | Yes      | string   | Device unique identifier.                                                                            |
| commandId          | Yes      | integer  | Device command identifier.                                                                           |
| command            | Yes      | object   | A DeviceCommand resource to update.                                                                  |
| command.command    | No       | string   | Command name.                                                                                        |
| command.timestamp  | No       | datetime | Command UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| command.parameters | No       | object   | Command parameters, a JSON object with an arbitrary structure.                                       |
| command.lifetime   | No       | integer  | Command lifetime, a number of seconds until this command expires.                                    |
| command.status     | No       | string   | Command status, as reported by device or related infrastructure.                                     |
| command.result     | No       | object   | Command execution result, an optional value that could be provided by device.                        |

## Response Topic and Payload

**Topic**

```text
dh/response/command/update@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object}
}
```

**Payload Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: command/update                                    |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
