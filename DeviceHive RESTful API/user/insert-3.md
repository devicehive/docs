---
title: "insert"
slug: "insert-3"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 05 2017 08:44:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Oct 23 2017 08:55:02 GMT+0000 (Coordinated Universal Time)"
---
Creates new user

## Request

**HTTP Request**

```text
POST /user
```

**Authorization**

Access JSON Web Token (ManageUser)

**Request Body**

In the request body, supply a [User](doc:user) resource.

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Required",
    "h-2": "Type",
    "h-3": "Description",
    "0-0": "login",
    "0-1": "Yes",
    "0-2": "string",
    "0-3": "User login using during authentication.",
    "1-0": "role",
    "1-1": "Yes",
    "1-2": "integer",
    "1-3": "User role. Available values:  \n  _ 0: Administrator role  \n  _ 1: Client role ",
    "2-0": "status",
    "2-1": "Yes",
    "2-2": "integer",
    "2-3": "User status. Available values:  \n  _ 0: The user is active  \n  _ 1: The user has been locked out due to invalid login attempts  \n  \\* 2: The user has been disabled ",
    "3-0": "password",
    "3-1": "Yes",
    "3-2": "string",
    "3-3": "User password",
    "4-0": "oldPassword",
    "4-1": "Yes",
    "4-2": "string",
    "4-3": "User old password. Required for non-admin users.",
    "5-0": "data",
    "5-1": "Yes",
    "5-2": "object",
    "5-3": "User data, a JSON object with an arbitrary structure."
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

If successful, this method returns a [User](doc:user) resource in the response body.

| Property Name | Type     | Description                                           |
| :------------ | :------- | :---------------------------------------------------- |
| id            | integer  | User identifier.                                      |
| lastLogin     | datetime | User last login timestamp (UTC).                      |
| data          | object   | User data, a JSON object with an arbitrary structure. |
| introReviewed | boolean  | Indicates if user reviewed an intro.                  |
