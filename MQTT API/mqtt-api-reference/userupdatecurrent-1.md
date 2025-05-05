---
title: "user/updateCurrent"
slug: "userupdatecurrent-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:58:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:31:05 GMT+0000 (Coordinated Universal Time)"
---
Updates an existing user.

Only administrators are allowed to update any property of any user. User-level accounts can only change their own password and data fields.

**Authorization**

Access JSON Web Token (UpdateCurrentUser)

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
    "user": {
        "login": {string},
        "role": {integer},
        "status": {integer},
        "password": {string},
        "data": {object},
        "introReviewed": {boolean}
        
    }
}
```

**Payload Parameters**

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
    "0-3": "Action name: user/updateCurrent",
    "1-0": "requestId",
    "1-1": "No",
    "1-2": "object",
    "1-3": "Request unique identifier, will be passed back in the response message.",
    "2-0": "user",
    "2-1": "Yes",
    "2-2": "object",
    "2-3": "User identifier. Use the 'current' keyword to update information of the current user.",
    "3-0": "user.login",
    "3-1": "No",
    "3-2": "string",
    "3-3": "User login using during authentication.",
    "4-0": "user.role",
    "4-1": "No",
    "4-2": "integer",
    "4-3": "User role. Available values:  \n  _ 0: Administrator role  \n  _ 1: Client role ",
    "5-0": "user.status",
    "5-1": "No",
    "5-2": "integer",
    "5-3": "User status. Available values:  \n  _ 0: The user is active  \n  _ 1: The user has been locked out due to invalid login attempts  \n  \\* 2: The user has been disabled ",
    "6-0": "user.password",
    "6-1": "No",
    "6-2": "string",
    "6-3": "User new password",
    "7-0": "user.data",
    "7-1": "No",
    "7-2": "object",
    "7-3": "User data, a JSON object with an arbitrary structure.",
    "8-0": "user.introReviewed",
    "8-1": "No",
    "8-2": "boolean",
    "8-3": "Indicates if user reviewed an intro."
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


## Response Topic and Payload

**Topic**

```text
dh/response/user/updateCurrent@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "requestId": {object},
     "status": {string}
}
```

**Payload Parameters**

| Property Name | Type   | Description                                                             |
| :------------ | :----- | :---------------------------------------------------------------------- |
| action        | string | Action name: user/updateCurrent                                         |
| requestId     | object | Request unique identifier, will be passed back in the response message. |
| status        | string | Operation execution status (success or error).                          |
