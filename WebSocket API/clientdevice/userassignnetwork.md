---
title: "user/assignNetwork"
slug: "userassignnetwork"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Jul 31 2017 07:31:04 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Associates network with the user.

## Request Message

**Authorization**

Access JSON Web Token (ManageNetwork)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "userId": {long},
    "networkId": {long}
}
```

**Message Parameters**

| Parameter Name | Required | Type   | Description                                                             |
| :------------- | :------- | :----- | :---------------------------------------------------------------------- |
| action         | Yes      | string | Action name: user/assignNetwork                                         |
| requestId      | No       | object | Request unique identifier, will be passed back in the response message. |
| userId         | Yes      | long   | User identifier.                                                        |
| networkId      | Yes      | long   | Network identifier.                                                     |

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
| action        | string | Action name: user/assignNetwork                                |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
