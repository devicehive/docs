---
title: "devicetype/delete"
slug: "devicetypedelete-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:56:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:28:37 GMT+0000 (Coordinated Universal Time)"
---
Deletes an existing network.

**Authorization**

Access JSON Web Token (ManageDeviceType)

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
    "deviceTypeId": {int}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: devicetype/delete                                          |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| deviceTypeId  | Yes      | int    | Device type identifier.                                                 |

## Response Topic and Payload

**Topic**

```text
dh/response/devicetype/delete@{clientId}
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
| action        | string | Action name: devicetype/delete                                 |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
