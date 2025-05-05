---
title: "user/getDeviceTypes"
slug: "usergetdevicetypes"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed May 23 2018 10:56:54 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 23 2018 11:13:09 GMT+0000 (Coordinated Universal Time)"
---
Gets information about all user/device type associations.

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
| action         | Yes      | string  | Action name: user/getDeviceTypes                                        |
| requestId      | No       | object  | Request unique identifier, will be passed back in the response message. |
| userId         | Yes      | integer | User identifier                                                         |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "deviceTypes": [{
    		"id": {int},
        "name": {string},
        "description": {string}
    }]
}
```

**Message Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: user/getDeviceTypes                               |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
