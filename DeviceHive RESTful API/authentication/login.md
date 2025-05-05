---
title: "login"
slug: "login"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 13:01:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Creates and returns access and refresh tokens for the given user.

## Request

**HTTP Request**

```text
POST /token
```

**Authorization**  
None

**Request Body**  
In the request body, supply user credentials.

| Property Name | Required | Type   | Description    |
| :------------ | :------- | :----- | :------------- |
| login         | Yes      | string | User login.    |
| password      | Yes      | string | User password. |

## Response

If successful, this method returns a pair of access and refresh tokens.

| Property Name | Type   | Description             |
| :------------ | :----- | :---------------------- |
| accessToken   | string | Access JSON Web Token.  |
| refreshToken  | string | Refresh JSON Web Token. |
