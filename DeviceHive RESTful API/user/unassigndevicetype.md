---
title: "unassignDeviceType"
slug: "unassigndevicetype"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed May 23 2018 11:25:50 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Removes association between device type and user.

## Request

**HTTP Request**

```text
DELETE /user/{id}/devicetype/{deviceTypeId}
```

**Parameters**

| Parameter Name | Required | Type    | Description             |
| :------------- | :------- | :------ | :---------------------- |
| id             | Yes      | integer | User identifier.        |
| deviceTypeId   | Yes      | integer | Device type identifier. |

**Authorization**

Access JSON Web Token (ManageUser)

**Request Body**

In the request body, supply the empty object.

## Response

If successful, this method returns an empty response body.
