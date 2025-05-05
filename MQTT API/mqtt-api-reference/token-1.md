---
title: "token"
slug: "token-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:02:06 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:33:14 GMT+0000 (Coordinated Universal Time)"
---
Creates access and refresh tokens by login and password.

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
    "login": {string},
    "password": {string}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: token                                                      |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| login         | Yes      | string | User login.                                                             |
| password      | Yes      | string | User password.                                                          |

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
    "requestId": {object},
    "accessToken": {string},
    "refreshToken": {string}
}
```

**Payload Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: token                                             |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
| accessToken   | string | JSON Web Token for authorization.                              |
| refreshToken  | string | JSON Web Token for refreshing access token.                    |
