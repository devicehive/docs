---
title: "user/delete"
slug: "userdelete"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Jul 31 2017 07:28:50 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Deletes an existing user.

## Request Message

**Authorization**

Access JSON Web Token (ManageUser)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "userId": {string}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: user/delete                                                |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| userId        | Yes      | string | User unique identifier.                                                 |

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
| action        | string | Action name: user/delete                                       |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
