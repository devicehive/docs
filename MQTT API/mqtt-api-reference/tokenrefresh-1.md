---
title: "token/refresh"
slug: "tokenrefresh-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:02:56 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:33:57 GMT+0000 (Coordinated Universal Time)"
---
Refreshes access token by refresh token.

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
    "refreshToken": {string}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: token/refresh                                              |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| refreshToken  | Yes      | string | User JSON Web Refresh Token.                                            |

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
    "accessToken": {string}
}
```

**Payload Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: token/refresh                                     |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
| accessToken   | string | JSON Web Token for authorization.                              |
