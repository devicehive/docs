---
title: "device/delete"
slug: "devicedelete"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jul 14 2017 14:55:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Deletes an existing device.

## Request Message

**Authorization**

Access JSON Web Token (RegisterDevice)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: device/delete                                              |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| deviceId      | Yes      | string | Device unique identifier.                                               |

## Server Message

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
| action        | string | Action name: device/delete                                     |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
