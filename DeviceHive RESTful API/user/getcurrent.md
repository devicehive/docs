---
title: "getCurrent"
slug: "getcurrent"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 05 2017 08:45:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets information about user and its assigned networks.

Only administrators are allowed to get information about any user. User-level accounts can only retrieve information about themselves.

## Request

**HTTP Request**

```text
GET /user/current
```

**Authorization**

Access JSON Web Token (GetCurrentUser)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns a [User](doc:user)  resource in the response body.

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "id",
    "0-1": "integer",
    "0-2": "User identifier.",
    "1-0": "login",
    "1-1": "string",
    "1-2": "User login using during authentication.",
    "2-0": "role",
    "2-1": "integer",
    "2-2": "User role. Available values:  \n  _ 0: Administrator role  \n  _ 1: Client role ",
    "3-0": "status",
    "3-1": "integer",
    "3-2": "User status. Available values:  \n  _ 0: The user is active  \n  _ 1: The user has been locked out due to invalid login attempts  \n  \\* 2: The user has been disabled ",
    "4-0": "lastLogin",
    "4-1": "datetime",
    "4-2": "User last login timestamp (UTC).",
    "5-0": "networks",
    "5-1": "array",
    "5-2": "Array of networks associated with the user",
    "6-0": "networks\\[].id",
    "6-1": "integer",
    "6-2": "Network identifier.",
    "7-0": "networks\\[].name",
    "7-1": "string",
    "7-2": "Network display name.",
    "8-0": "networks\\[].description",
    "8-1": "string",
    "8-2": "Network description.",
    "9-0": "data",
    "9-1": "object",
    "9-2": "User data, a JSON object with an arbitrary structure.",
    "10-0": "introReviewed",
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
