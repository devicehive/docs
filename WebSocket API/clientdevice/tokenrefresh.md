---
title: "token/refresh"
slug: "tokenrefresh"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Sat Jul 15 2017 13:00:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Refreshes access token by refresh token.

## Request Message

**Authorization**

None

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "refreshToken": {string}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: token/refresh                                              |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| refreshToken  | Yes      | string | User JSON Web Refresh Token.                                            |

## Response Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "accessToken": {string}
}
```

**Message Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: token/refresh                                     |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
| accessToken   | string | JSON Web Token for authorization.                              |
