---
title: "command/subscribe"
slug: "commandsubscribe"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:54:03 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:26:07 GMT+0000 (Coordinated Universal Time)"
---
Subscribes to device commands. After subscription is completed, the server will start to send command/insert messages to the connected user.

**Authorization**

Access JSON Web Token (GetDeviceCommand)

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
    "timestamp": {datetime},
    "deviceId": {string},
    "networkIds": {array},
    "deviceTypeIds": {array},
    "returnUpdatedCommands": {boolean},
    "names": {array}
    "limit": {integer}
}
```

**Payload Parameters**

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

## Response Topic and Payload

**Topic**

```text
dh/response/command/subscribe@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "subscriptionId": {long}
}
```

**Payload Parameters**

| Property Name  | Type   | Description                                                    |
| :------------- | :----- | :------------------------------------------------------------- |
| action         | string | Action name: command/subscribe                                 |
| status         | string | Operation execution status (success or error).                 |
| requestId      | object | Request unique identifier as specified in the request message. |
| subscriptionId | long   | A unique identifier of the subscription made.                  |
