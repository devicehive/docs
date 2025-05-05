---
title: "unassignNetwork"
slug: "unassignnetwork"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 05 2017 08:46:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Removes association between network and user.

## Request

**HTTP Request**

DELETE /user/{id}/network/{networkId}  
**Parameters**

| Parameter Name | Required | Type    | Description        |
| :------------- | :------- | :------ | :----------------- |
| id             | Yes      | integer | User identifier    |
| networkId      | Yes      | integer | Network identifier |

**Authorization**

Access JSON Web Token (ManageUser)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns an empty response body.
