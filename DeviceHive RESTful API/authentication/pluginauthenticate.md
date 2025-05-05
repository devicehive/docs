---
title: "plugin/authenticate"
slug: "pluginauthenticate"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Nov 17 2017 14:53:21 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Nov 17 2017 14:55:38 GMT+0000 (Coordinated Universal Time)"
---
Creates and returns access and refresh tokens for the given user and access rights.

## Request

**HTTP Request**

```text
POST /token/plugin/authenticate
```

**Authorization**

Access JSON Web Token (ManagePlugin)

**Parameters**

| Property Name | Required | Type   | Description       |
| :------------ | :------- | :----- | :---------------- |
| token         | Yes      | string | Jwt Plugin Token. |

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns a payload for JWT Plugin Token.

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "tpc",
    "0-1": "string",
    "0-2": "Permitted topic name.",
    "1-0": "e",
    "1-1": "string",
    "1-2": "Expiration date (UTC).",
    "2-0": "t",
    "2-1": "integer",
    "2-2": "Token type:  \n0 - REFRESH,  \n1 - ACCESS."
  },
  "cols": 3,
  "rows": 3,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]
