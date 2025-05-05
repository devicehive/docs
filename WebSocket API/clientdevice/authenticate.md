---
title: "authenticate"
slug: "authenticate"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 12 2017 19:18:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Authenticates a client / device by a JSON Web Token. After successful authentication, all subsequent messages may exclude JSON Web Token parameter.

## Request Message

**Authorization**

None

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "token": {string}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: authenticate                                               |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| token         | Yes      | object | Access JSON Web Token.                                                  |

## Response Message

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
| action        | string | Action name: authenticate                                      |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
