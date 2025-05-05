---
title: "delete"
slug: "delete-3"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 05 2017 08:44:49 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Deletes an existing user.

## Request

**HTTP Request**

```text
DELETE /user/{id}
```

**Parameters**

Parameter Name	Required	Type	Description  
id	Yes	integer	User identifier.  
**Authorization**

Access JSON Web Token (ManageUser)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns an empty response body.
