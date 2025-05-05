---
title: "user/list"
slug: "userlist"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Jul 31 2017 07:26:36 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets list of users.

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
    "status": {integer},
    "sortField": {string},
    "sortOrder": {string},
    "take": {integer},
    "skip": {integer}
}
```

**Parameters**

| Parameter Name | Required | Type    | Description                                                             |
| :------------- | :------- | :------ | :---------------------------------------------------------------------- |
| action         | Yes      | string  | Action name: user/list                                                  |
| requestId      | No       | object  | Request unique identifier, will be passed back in the response message. |
| login          | No       | string  | Filter by user login                                                    |
| loginPattern   | No       | string  | Filter by user login pattern                                            |
| role           | No       | integer | Filter by user role. 0 is Administrator, 1 is Client.                   |
| status         | No       | integer | Filter by user status. 0 is Active, 1 is Locked Out, 2 is Disabled.     |
| sortField      | No       | string  | Result list sort field. Available values are ID and Login.              |
| sortOrder      | No       | string  | Result list sort order. Available values are ASC and DESC.              |
| take           | No       | integer | Number of records to take from the result list.                         |
| skip           | No       | integer | Number of records to skip from the result list.                         |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "status": {string},
    "users": [{
        "id": {long},
        "login": {string},
        "role": {integer},
        "status": {integer},
        "lastLogin": {datetime},
        "data": {object},
        "introReviewed": {boolean}
    }]
}
```

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "id",
    "0-1": "long",
    "0-2": "User identifier.",
    "1-0": "login",
    "1-1": "string",
    "1-2": "User login using during authentication.",
    "2-0": "role",
    "2-1": "integer",
    "2-2": "User role. Available values:  \n0: Administrator role  \n1: Client role",
    "3-0": "status",
    "3-1": "integer",
    "3-2": "User status. Available values:  \n0: The user is active  \n1: The user has been locked out due to invalid login attempts  \n2: The user has been disabled",
    "4-0": "lastLogin",
    "4-1": "datetime",
    "4-2": "User last login timestamp (UTC).",
    "5-0": "data",
    "5-1": "object",
    "5-2": "User data, a JSON object with an arbitrary structure.",
    "6-0": "introReviewed",
    "6-1": "boolean",
    "6-2": "Indicates if user reviewed an intro."
  },
  "cols": 3,
  "rows": 7,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]
