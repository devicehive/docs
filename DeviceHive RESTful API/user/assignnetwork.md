---
title: "assignNetwork"
slug: "assignnetwork"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 05 2017 08:46:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Associates network with the user.

## Request

**HTTP Request**

```text
PUT /user/{id}/network/{networkId}
```

**Parameters**

| Parameter Name | Required | Type    | Description         |
| :------------- | :------- | :------ | :------------------ |
| id             | Yes      | integer | User identifier.    |
| networkId      | Yes      | integer | Network identifier. |

**Authorization**

Access JSON Web Token (ManageUser)

**Request Body**

In the request body, supply the empty object.

## Response

If successful, this method returns an empty response body.
