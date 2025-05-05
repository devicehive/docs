---
title: "updateCurrent"
slug: "updatecurrent"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 05 2017 08:45:46 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Updates an existing user.

Only administrators are allowed to update any property of any user. User-level accounts can only change their own password and data fields.

## Request

**HTTP Request**

```text
PUT /user/current
```

**Authorization**

Access JSON Web Token (UpdateCurrentUser)

**Request Body**

In the request body, supply a [User](doc:user)  resource.

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Required",
    "h-2": "Type",
    "h-3": "Description",
    "0-0": "login",
    "0-1": "No",
    "0-2": "string",
    "0-3": "User login using during authentication.",
    "1-0": "role",
    "1-1": "No",
    "1-2": "integer",
    "1-3": "User role. Available values:  \n  _ 0: Administrator role  \n  _ 1: Client role ",
    "2-0": "status",
    "2-1": "No",
    "2-2": "integer",
    "2-3": "User status. Available values:  \n  _ 0: The user is active  \n  _ 1: The user has been locked out due to invalid login attempts  \n  \\* 2: The user has been disabled ",
    "3-0": "password",
    "3-1": "No",
    "3-2": "string",
    "3-3": "User new password",
    "4-0": "data",
    "4-1": "No",
    "4-2": "object",
    "4-3": "User data, a JSON object with an arbitrary structure.",
    "5-0": "introReviewed",
    "5-1": "No",
    "5-2": "boolean",
    "5-3": "Indicates if user reviewed an intro."
  },
  "cols": 4,
  "rows": 6,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Response

If successful, this method returns an empty response body.
