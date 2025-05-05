---
title: "command/unsubscribe"
slug: "commandunsubscribe-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:54:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:26:19 GMT+0000 (Coordinated Universal Time)"
---
Unsubscribes from device commands.

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
    "subscriptionId": {integer}
}
```

**Payload Parameters**

| Property Name  | Required | Type    | Description                                                                                                                       |
| :------------- | :------- | :------ | :-------------------------------------------------------------------------------------------------------------------------------- |
| action         | Yes      | string  | Action name: command/unsubscribe                                                                                                  |
| requestId      | No       | object  | Request unique identifier, will be passed back in the response message.                                                           |
| subscriptionId | No       | integer | An identifier of the previously made subscription to unsubscribe from. If not specified, unsubscribe from all user subscriptions. |

## Response Topic and Payload

**Topic**

```text
dh/response/command/unsubscribe@{clientId}
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
| action        | string | Action name: command/unsubscribe                               |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
