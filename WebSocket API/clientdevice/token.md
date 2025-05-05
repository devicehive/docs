---
title: "token"
slug: "token"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Sat Jul 15 2017 12:59:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Creates access and refresh tokens by login and password.

## Request Message

**Authorization**

None

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "login": {string},
    "password": {string}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: token                                                      |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| login         | Yes      | string | User login.                                                             |
| password      | Yes      | string | User password.                                                          |

## Response Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "accessToken": {string},
    "refreshToken": {string}
}
```

**Message Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: token                                             |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
| accessToken   | string | JSON Web Token for authorization.                              |
| refreshToken  | string | JSON Web Token for refreshing access token.                    |
