---
title: "user/assignNetwork"
slug: "userassignnetwork-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:00:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:31:34 GMT+0000 (Coordinated Universal Time)"
---
Associates network with the user.

**Authorization**

Access JSON Web Token (ManageNetwork)

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
    "userId": {long},
    "networkId": {long}
}
```

**Payload Parameters**

| Parameter Name | Required | Type   | Description                                                             |
| :------------- | :------- | :----- | :---------------------------------------------------------------------- |
| action         | Yes      | string | Action name: user/assignNetwork                                         |
| requestId      | No       | object | Request unique identifier, will be passed back in the response message. |
| userId         | Yes      | long   | User identifier.                                                        |
| networkId      | Yes      | long   | Network identifier.                                                     |

## Response Topic and Payload

**Topic**

```text
dh/response/user/assignNetwork@{clientId}
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
| action        | string | Action name: user/assignNetwork                                |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
