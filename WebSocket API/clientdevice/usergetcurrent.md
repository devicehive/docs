---
title: "user/getCurrent"
slug: "usergetcurrent"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Jul 31 2017 07:29:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets information about user and its assigned networks.

Only administrators are allowed to get information about any user. User-level accounts can only retrieve information about themselves.

## Request Message

**Authorization**

Access JSON Web Token (GetCurrentUser)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object}
}
```

**Message Parameters**

|           |     |        |                                                                         |
| :-------- | :-- | :----- | :---------------------------------------------------------------------- |
| action    | Yes | string | Action name: user/getCurrent                                            |
| requestId | No  | object | Request unique identifier, will be passed back in the response message. |
| userId    | Yes | long   | User identifier.                                                        |

## Server Message

If successful, this method returns a [User](doc:user)  resource in the response body.

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "current": {
        "id": {string},
        "login": {string},
        "role": {integer},
        "status": {integer},
        "lastLogin": {datetime},
        "networks": [{
            id: {integer},
            name: {string},
            description: {string}
        }],
        "data": {object},
        "introReviewed": {boolean}
    }
}
```

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "action",
    "0-1": "string",
    "0-2": "Action name: user/getCurrent",
    "1-0": "status",
    "1-1": "string",
    "1-2": "Operation execution status (success or error).",
    "2-0": "requestId",
    "2-1": "object",
    "2-2": "Request unique identifier as specified in the request message.",
    "3-0": "current",
    "3-1": "object",
    "3-2": "Current user object.",
    "4-0": "current.id",
    "4-1": "integer",
    "4-2": "User identifier.",
    "5-0": "current.login",
    "5-1": "string",
    "5-2": "User login using during authentication.",
    "6-0": "current.role",
    "6-1": "integer",
    "6-2": "User role. Available values:  \n  _ 0: Administrator role  \n  _ 1: Client role ",
    "7-0": "current.status",
    "7-1": "integer",
    "7-2": "User status. Available values:  \n  _ 0: The user is active  \n  _ 1: The user has been locked out due to invalid login attempts  \n  \\* 2: The user has been disabled ",
    "8-0": "current.lastLogin",
    "8-1": "datetime",
    "8-2": "User last login timestamp (UTC).",
    "9-0": "current.networks",
    "9-1": "array",
    "9-2": "Array of networks associated with the user",
    "10-0": "current.networks\\[].id",
    "10-1": "integer",
    "10-2": "Network identifier.",
    "11-0": "current.networks\\[].name",
    "11-1": "string",
    "11-2": "Network display name.",
    "12-0": "current.networks\\[].description",
    "12-1": "string",
    "12-2": "Network description.",
    "13-0": "current.data",
    "13-1": "object",
    "13-2": "User data, a JSON object with an arbitrary structure.",
    "14-0": "current.introReviewed",
    "14-1": "boolean",
    "14-2": "Indicates if user reviewed an intro."
  },
  "cols": 3,
  "rows": 15,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]
