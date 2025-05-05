---
title: "user/assignDeviceType"
slug: "userassigndevicetype"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed May 23 2018 10:36:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Associates device type with the user.

## Request Message

**Authorization**

Access JSON Web Token (ManageNetwork)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "userId": {long},
    "deviceTypeId": {long}
}
```

**Message Parameters**

| Parameter Name | Required | Type   | Description                                                             |
| :------------- | :------- | :----- | :---------------------------------------------------------------------- |
| action         | Yes      | string | Action name: user/assignDeviceType                                      |
| requestId      | No       | object | Request unique identifier, will be passed back in the response message. |
| userId         | Yes      | long   | User identifier.                                                        |
| deviceTypeId   | Yes      | long   | Device type identifier.                                                 |

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
| action        | string | Action name: user/assignDeviceType                             |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
