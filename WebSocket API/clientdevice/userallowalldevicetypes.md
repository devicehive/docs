---
title: "user/allowAllDeviceTypes"
slug: "userallowalldevicetypes"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed May 23 2018 11:17:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Allows all device types for user.

## Request Message

**Authorization**

Access JSON Web Token (ManageUser)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "userId": {long}
}
```

| Parameter Name | Required | Type    | Description                                                             |
| :------------- | :------- | :------ | :---------------------------------------------------------------------- |
| action         | Yes      | string  | Action name: user/allowAllDeviceTypes                                   |
| requestId      | No       | object  | Request unique identifier, will be passed back in the response message. |
| userId         | Yes      | integer | User identifier                                                         |

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
| action        | string | Action name: user/allowAllDeviceTypes                          |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
