---
title: "device/delete"
slug: "devicedelete-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:55:11 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:27:31 GMT+0000 (Coordinated Universal Time)"
---
Deletes an existing device.

**Authorization**

Access JSON Web Token (RegisterDevice)

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
    "deviceId": {string}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: device/delete                                              |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| deviceId      | Yes      | string | Device unique identifier.                                               |

## Response Topic and Payload

**Topic**

```text
dh/response/device/delete@{clientId}
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
| action        | string | Action name: device/delete                                     |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
