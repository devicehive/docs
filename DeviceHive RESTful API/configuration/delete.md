---
title: "delete"
slug: "delete"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 07:27:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Deletes a property.

## Request

**HTTP Request**

```text
DELETE /configuration/{name}
```

**Parameters**

| Parameter Name | Required | Type   | Description                   |
| :------------- | :------- | :----- | :---------------------------- |
| name           | Yes      | string | Configuration parameter name. |

**Authorization**

JSON Web Token (ManageConfiguration)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns an empty response body.
