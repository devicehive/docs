---
title: "plugin/create"
slug: "plugincreate"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Nov 17 2017 14:36:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Creates and returns access and refresh tokens for the given user and access rights.

## Request

**HTTP Request**

```text
POST /token/plugin/create
```

**Authorization**

Access JSON Web Token (ManagePlugin)

**Request Body**

In the request body, supply user identifier, rights and expiration date.

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Required",
    "h-2": "Type",
    "h-3": "Description",
    "0-0": "tpc",
    "0-1": "Yes",
    "0-2": "string",
    "0-3": "Permitted topic name.",
    "1-0": "e",
    "1-1": "No",
    "1-2": "datetime",
    "1-3": "Expiration date (UTC).",
    "2-0": "t",
    "2-1": "Yes",
    "2-2": "integer",
    "2-3": "Token type:  \n0 - REFRESH,  \n1 - ACCESS."
  },
  "cols": 4,
  "rows": 3,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Response

If successful, this method returns a pair of access and refresh plugin tokens.

| Property Name | Type   | Description                    |
| :------------ | :----- | :----------------------------- |
| accessToken   | string | Access JSON Plugin Web Token.  |
| refreshToken  | string | Refresh JSON Plugin Web Token. |
