---
title: "network/delete"
slug: "networkdelete-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:57:11 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:29:39 GMT+0000 (Coordinated Universal Time)"
---
Deletes an existing network.

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
    "networkId": {int}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: network/delete                                             |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| networkId     | Yes      | int    | Network unique identifier.                                              |

## Response Topic and Payload

**Topic**

```text
dh/response/network/delete@{clientId}
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
| action        | string | Action name: network/delete                                    |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
