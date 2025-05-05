---
title: "delete"
slug: "delete-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 09:59:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Deletes an existing device.

## Request

**HTTP Request**

```text
DELETE /device/{id}
```

**Parameters**

| Parameter Name | Required | Type   | Description               |
| :------------- | :------- | :----- | :------------------------ |
| id             | Yes      | string | Device unique identifier. |

**Authorization**

Access JSON Web Token (RegisterDevice)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns an empty response body.
