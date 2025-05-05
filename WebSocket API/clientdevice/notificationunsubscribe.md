---
title: "notification/unsubscribe"
slug: "notificationunsubscribe"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Sat Jul 15 2017 08:17:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 23:41:31 GMT+0000 (Coordinated Universal Time)"
---
Unsubscribes from device notifications.

## Request Message

**Authorization**

Access JSON Web Token (GetDeviceNotification)

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
| action         | Yes      | string  | Action name: notification/unsubscribe                                                                                             |
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
| action        | string | Action name: notification/unsubscribe                          |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
