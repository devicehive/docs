---
title: "user/count"
slug: "usercount"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jan 09 2018 14:50:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jan 09 2018 14:53:31 GMT+0000 (Coordinated Universal Time)"
---
Gets count of users.

## Request Message

**Authorization**

Access JSON Web Token (ManageUser)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "login": {string},
    "loginPattern": {string},
    "role": {integer},
    "status": {integer}
}
```

**Parameters**

| Parameter Name | Required | Type    | Description                                                             |
| :------------- | :------- | :------ | :---------------------------------------------------------------------- |
| action         | Yes      | string  | Action name: user/count                                                 |
| requestId      | No       | object  | Request unique identifier, will be passed back in the response message. |
| login          | No       | string  | Filter by user login                                                    |
| loginPattern   | No       | string  | Filter by user login pattern                                            |
| role           | No       | integer | Filter by user role. 0 is Administrator, 1 is Client.                   |
| status         | No       | integer | Filter by user status. 0 is Active, 1 is Locked Out, 2 is Disabled.     |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "status": {string},
    "count": {integer}
}
```

| Property Name | Type    | Description                                                    |
| :------------ | :------ | :------------------------------------------------------------- |
| action        | string  | Action name: user/count                                        |
| requestId     | object  | Request unique identifier as specified in the request message. |
| status        | string  | Operation execution status (success or error).                 |
| count         | integer | Number of users that match the filters.                        |
