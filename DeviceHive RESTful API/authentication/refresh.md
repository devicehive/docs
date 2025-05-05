---
title: "refresh"
slug: "refresh"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 13:15:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Nov 17 2017 14:30:17 GMT+0000 (Coordinated Universal Time)"
---
Creates new access token for the given refresh token. This endpoint refreshes as User Jwt Token and also Plugin Jwt Token.

## Request

**HTTP Request**

```text
POST /token/refresh
```

**Authorization**

None

**Request Body**

In the request body, supply a refresh JSON Web Token.

| Property Name | Required | Type   | Description     |
| :------------ | :------- | :----- | :-------------- |
| refreshToken  | Yes      | string | JSON Web Token. |
