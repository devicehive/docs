---
title: "command/subscribe"
slug: "commandsubscibe"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 12 2017 19:19:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Jan 22 2018 16:07:03 GMT+0000 (Coordinated Universal Time)"
---
Subscribes to device commands. After subscription is completed, the server will start to send command/insert messages to the connected user.

## Request Message

**Authorization**

Access JSON Web Token (GetDeviceCommand)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "timestamp": {datetime},
    "deviceId": {string},
    "networkIds": {array},
    "deviceTypeIds": {array},
    "returnUpdatedCommands": {boolean},
    "names": {array}
    "limit": {integer}
}
```

**Message Parameters**

| Property Name         | Required | Type     | Description                                                                                                                                                                          |
| :-------------------- | :------- | :------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| action                | Yes      | string   | Action name: command/subscribe                                                                                                                                                       |
| requestId             | No       | object   | Request unique identifier, will be passed back in the response message.                                                                                                              |
| timestamp             | No       | datetime | UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)) of the last received command. If not specified, the server's timestamp is taken instead. |
| deviceId              | No       | string   | A unique device identifier to subscribe to. If not specified, the subscription is made to all accessible devices.                                                                    |
| networkIds            | No       | array    | Array of network unique identifiers to subscribe to.                                                                                                                                 |
| deviceTypeIds         | No       | array    | Array of device type unique identifiers to subscribe to.                                                                                                                             |
| returnUpdatedCommands | No       | boolean  | Checks if updated commands should be returned. If not specified, default value is false.                                                                                             |
| names                 | No       | array    | Array of command names to subscribe to.                                                                                                                                              |
| limit                 | No       | object   | Limits the number of commands for a subscription.                                                                                                                                    |

## Response Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "subscriptionId": {long}
}
```

**Message Parameters**

| Property Name  | Type   | Description                                                    |
| :------------- | :----- | :------------------------------------------------------------- |
| action         | string | Action name: command/subscribe                                 |
| status         | string | Operation execution status (success or error).                 |
| requestId      | object | Request unique identifier as specified in the request message. |
| subscriptionId | long   | A unique identifier of the subscription made.                  |
