---
title: "command/update"
slug: "commandupdate"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 12 2017 19:20:23 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Apr 19 2018 08:34:17 GMT+0000 (Coordinated Universal Time)"
---
Updates an existing device command on behalf of device.

## Request Message

**Authorization**

Access JSON Web Token (UpdateDeviceCommand)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string},
    "commandId": {integer},
    "command": {
        "status": {string},
        "result": {object}
    }
}
```

**Message Parameters**

| Property Name  | Required | Type    | Description                                                                   |
| :------------- | :------- | :------ | :---------------------------------------------------------------------------- |
| action         | Yes      | string  | Action name: command/update                                                   |
| requestId      | No       | object  | Request unique identifier, will be passed back in the response message.       |
| deviceId       | Yes      | string  | Device unique identifier.                                                     |
| commandId      | Yes      | integer | Device command identifier.                                                    |
| command        | Yes      | object  | A DeviceCommand resource to update.                                           |
| command.status | No       | string  | Command status, as reported by device or related infrastructure.              |
| command.result | No       | object  | Command execution result, an optional value that could be provided by device. |

## Response Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object}
}
```

**Message Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: command/update                                    |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
