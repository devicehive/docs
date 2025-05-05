---
title: "authenticate"
slug: "authenticate-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:47:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 13:06:08 GMT+0000 (Coordinated Universal Time)"
---
Authenticates a client / device by a JSON Web Token. After successful authentication, all subsequent messages may exclude JSON Web Token parameter.

**Authorization**

None

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
    "token": {string}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: authenticate                                               |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| token         | Yes      | object | Access JSON Web Token.                                                  |

## Response Topic and Payload

**Topic**

```text
dh/response/authenticate@{clientId}
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
| action        | string | Action name: authenticate                                      |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
