---
title: "user/delete"
slug: "userdelete-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:58:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:30:45 GMT+0000 (Coordinated Universal Time)"
---
Deletes an existing user.

**Authorization**

Access JSON Web Token (ManageUser)

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
    "userId": {string}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: user/delete                                                |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| userId        | Yes      | string | User unique identifier.                                                 |

## Response Topic and Payload

**Topic**

```text
dh/response/user/delete@{clientId}
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
| action        | string | Action name: user/delete                                       |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
