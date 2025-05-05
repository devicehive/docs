---
title: "command/unsubscribe"
slug: "commandunsubscribe"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 12 2017 19:20:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 23:30:41 GMT+0000 (Coordinated Universal Time)"
---
Unsubscribes from device commands.

## Request Message

**Authorization**  
Access JSON Web Token (GetDeviceCommand)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "subscriptionId": {integer}
}
```

**Message Parameters**

| Property Name  | Required | Type    | Description                                                                                                                       |
| :------------- | :------- | :------ | :-------------------------------------------------------------------------------------------------------------------------------- |
| action         | Yes      | string  | Action name: command/unsubscribe                                                                                                  |
| requestId      | No       | object  | Request unique identifier, will be passed back in the response message.                                                           |
| subscriptionId | No       | integer | An identifier of the previously made subscription to unsubscribe from. If not specified, unsubscribe from all user subscriptions. |

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
| action        | string | Action name: command/unsubscribe                               |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
