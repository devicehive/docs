---
title: "user/count"
slug: "usercount-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:57:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:30:01 GMT+0000 (Coordinated Universal Time)"
---
Gets count of users.

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
    "login": {string},
    "loginPattern": {string},
    "role": {integer},
    "status": {integer}
}
```

**Payload Parameters**

| Parameter Name | Required | Type    | Description                                                             |
| :------------- | :------- | :------ | :---------------------------------------------------------------------- |
| action         | Yes      | string  | Action name: user/count                                                 |
| requestId      | No       | object  | Request unique identifier, will be passed back in the response message. |
| login          | No       | string  | Filter by user login                                                    |
| loginPattern   | No       | string  | Filter by user login pattern                                            |
| role           | No       | integer | Filter by user role. 0 is Administrator, 1 is Client.                   |
| status         | No       | integer | Filter by user status. 0 is Active, 1 is Locked Out, 2 is Disabled.     |

## Response Topic and Payload

**Topic**

```text
dh/response/user/count@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "status": {string},
    "count": {integer}
}
```

**Payload Parameters**

| Property Name | Type    | Description                                                    |
| :------------ | :------ | :------------------------------------------------------------- |
| action        | string  | Action name: user/count                                        |
| requestId     | object  | Request unique identifier as specified in the request message. |
| status        | string  | Operation execution status (success or error).                 |
| count         | integer | Number of users that match the filters.                        |
