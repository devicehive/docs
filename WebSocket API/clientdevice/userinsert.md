---
title: "user/insert"
slug: "userinsert"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Jul 31 2017 07:27:47 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Creates new user

## Request Message

**Authorization**

Access JSON Web Token (ManageUser)

**Message Representation**

In the request body, supply a [User](doc:user) resource.

```text
{
    "action": {string},
    "requestId": {object},
    "user": {
        "login": {string},
        "role": {integer},
        "status": {integer},
        "password": {string},
        "oldPassword": {string},
        "data": {object}
    }
}
```

**Message Parameters**

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Required",
    "h-2": "Type",
    "h-3": "Description",
    "0-0": "action",
    "0-1": "Yes",
    "0-2": "string",
    "0-3": "Action name: user/insert",
    "1-0": "requestId",
    "1-1": "No",
    "1-2": "object",
    "1-3": "Request unique identifier, will be passed back in the response message.",
    "2-0": "user",
    "2-1": "Yes",
    "2-2": "object",
    "2-3": "User object",
    "3-0": "user.login",
    "3-1": "Yes",
    "3-2": "string",
    "3-3": "User login using during authentication.",
    "4-0": "user.role",
    "4-1": "Yes",
    "4-2": "integer",
    "4-3": "User role. Available values:  \n  _ 0: Administrator role  \n  _ 1: Client role ",
    "5-0": "user.status",
    "5-1": "Yes",
    "5-2": "integer",
    "5-3": "User status. Available values:  \n  _ 0: The user is active  \n  _ 1: The user has been locked out due to invalid login attempts  \n  \\* 2: The user has been disabled ",
    "6-0": "user.password",
    "6-1": "Yes",
    "6-2": "string",
    "6-3": "User password",
    "7-0": "user.oldPassword",
    "7-1": "Yes",
    "7-2": "string",
    "7-3": "User old password. Required for non-admin users.",
    "8-0": "user.data",
    "8-1": "Yes",
    "8-2": "object",
    "8-3": "User data, a JSON object with an arbitrary structure."
  },
  "cols": 4,
  "rows": 9,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Server Message

If successful, this method returns a [User](doc:user)  resource in the response body.

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "status": {string},
    "user": {
        "id": {integer},
        "login": {string},
        "role": {integer},
        "status": {integer},
        "lastLogin": {datetime},
        "data": {object},
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
    "0-2": "Action name: user/insert",
    "1-0": "requestId",
    "1-1": "object",
    "1-2": "Request unique identifier, will be passed back in the response message.",
    "2-0": "status",
    "2-1": "string",
    "2-2": "Operation execution status (success or error).",
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
    "6-2": "User role. Available values:  \n  _ 0: Administrator role  \n  _ 1: Client role ",
    "7-0": "user.status",
    "7-1": "integer",
    "7-2": "User status. Available values:  \n  _ 0: The user is active  \n  _ 1: The user has been locked out due to invalid login attempts  \n  \\* 2: The user has been disabled ",
    "8-0": "user.lastLogin",
    "8-1": "datetime",
    "8-2": "User last login timestamp (UTC).",
    "9-0": "user.data",
    "9-1": "object",
    "9-2": "User data, a JSON object with an arbitrary structure.",
    "10-0": "user.introReviewed",
    "10-1": "boolean",
    "10-2": "Indicates if user reviewed an intro."
  },
  "cols": 3,
  "rows": 11,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]
