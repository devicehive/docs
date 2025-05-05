---
title: "devicetype/delete"
slug: "devicetypedelete"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Jan 11 2018 11:11:17 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jan 11 2018 11:16:11 GMT+0000 (Coordinated Universal Time)"
---
Deletes an existing network.

## Request Message

**Authorization**

Access JSON Web Token (ManageDeviceType)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceTypeId": {int}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: devicetype/delete                                          |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| deviceTypeId  | Yes      | int    | Device type identifier.                                                 |

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
| action        | string | Action name: devicetype/delete                                 |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
