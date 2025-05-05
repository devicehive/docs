---
title: "delete"
slug: "delete-2"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 05 2017 06:44:01 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Deletes an existing device network.

## Request

**HTTP Request**

```text
DELETE /network/{id}
```

**Parameters**

| Parameter Name | Required | Type    | Description        |
| :------------- | :------- | :------ | :----------------- |
| id             | Yes      | integer | Network identifier |

**Authorization**

Access JSON Web Token (ManageNetwork)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns an empty response body.
