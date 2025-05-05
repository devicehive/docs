---
title: "delete"
slug: "delete-4"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 10 2018 14:31:46 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Deletes an existing device type.

## Request

**HTTP Request**

```text
DELETE /devicetype/{id}
```

**Parameters**

| Parameter Name | Required | Type    | Description             |
| :------------- | :------- | :------ | :---------------------- |
| id             | Yes      | integer | Device type identifier. |

**Authorization**

Access JSON Web Token (ManageDeviceType)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns an empty response body.
