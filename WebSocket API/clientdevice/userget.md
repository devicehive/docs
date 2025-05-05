---
title: "user/get"
slug: "userget"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Jul 31 2017 07:27:12 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets information about user and its assigned networks.

Only administrators are allowed to get information about any user. User-level accounts can only retrieve information about themselves.

## Request Message

**Authorization**

Access JSON Web Token (ManageUser)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "userId": {long}
}
```

**Message Parameters**

| Parameter Name | Required | Type   | Description                                                             |
| :------------- | :------- | :----- | :---------------------------------------------------------------------- |
| action         | Yes      | string | Action name: user/get                                                   |
| requestId      | No       | object | Request unique identifier, will be passed back in the response message. |
| userId         | Yes      | long   | User identifier.                                                        |

## Server Message

If successful, this method returns a [User](doc:user)  resource in the response body.

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "user": {
        "id": {string},
        "login": {string},
        "role": {integer},
        "status": {integer},
        "lastLogin": {datetime},
        "data": {object},
        "networks": [{
            id: {integer},
            name: {string},
            description: {string}
        }],
        "introReviewed": {boolean}
    }
}
```

**Message Parameters**

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "action",
    "0-1": "string",
    "0-2": "Action name: user/get",
    "1-0": "status",
    "1-1": "string",
    "1-2": "Operation execution status (success or error).",
    "2-0": "requestId",
    "2-1": "object",
    "2-2": "Request unique identifier as specified in the request message.",
    "3-0": "user",
    "3-1": "object",
    "3-2": "User object",
    "4-0": "user.id",
    "4-1": "integer",
    "4-2": "User identifier.",
    "5-0": "user.login",
    "5-1": "string",
    "5-2": "User login using during authentication.",
    "6-0": "user.role",
    "6-1": "integer",
    "6-2": "User role. Available values:  \n0: Administrator role  \n1: Client role",
    "7-0": "user.status",
    "7-1": "integer",
    "7-2": "User status. Available values:  \n0: The user is active  \n1: The user has been locked out due to invalid login attempts  \n2: The user has been disabled",
    "8-0": "user.lastLogin",
    "8-1": "datetime",
    "8-2": "User last login timestamp (UTC).",
    "9-0": "user.data",
    "9-1": "object",
    "9-2": "User data, a JSON object with an arbitrary structure.",
    "10-0": "user.networks",
    "10-1": "array",
    "10-2": "Array of networks associated with the user",
    "11-0": "user.networks\\[].network",
    "11-1": "object",
    "11-2": "Associated network object.",
    "12-0": "user.networks\\[].network.id",
    "12-1": "integer",
    "12-2": "Network identifier.",
    "13-0": "user.networks\\[].network.name",
    "13-1": "string",
    "13-2": "Network display name.",
    "14-0": "user.networks\\[].network.description",
    "14-1": "string",
    "14-2": "Network description.",
    "15-0": "user.introReviewed",
    "15-1": "boolean",
    "15-2": "Indicates if user reviewed an intro."
  },
  "cols": 3,
  "rows": 16,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]
