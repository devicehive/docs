---
title: "disallowAllDeviceTypes"
slug: "disallowalldevicetypes"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed May 23 2018 11:46:05 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Allows all device types for user.

## Request

**HTTP Request**

```text
DELETE /user/{id}/devicetype/all
```

**Parameters**

| Parameter Name | Required | Type    | Description      |
| :------------- | :------- | :------ | :--------------- |
| id             | Yes      | integer | User identifier. |

**Authorization**

Access JSON Web Token (ManageUser)

**Request Body**

In the request body, supply the empty object.

## Response

If successful, this method returns an empty response body.
