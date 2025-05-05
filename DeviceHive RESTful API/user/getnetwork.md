---
title: "getNetwork"
slug: "getnetwork"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 05 2017 08:45:56 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets information about user/network association.

## Request

**HTTP Request**

GET /user/{id}/network/{networkId}

**Parameters**

Parameter Name	Required	Type	Description  
id	Yes	integer	User identifier.  
networkId	Yes	integer	Network identifier.

| Parameter Name | Required | Type    | Description        |
| :------------- | :------- | :------ | :----------------- |
| id             | Yes      | integer | User identifier    |
| networkId      | Yes      | integer | Network identifier |

**Authorization**

Access JSON Web Token (ManageUser)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns the following structure in the response body.

| Property Name       | Type    | Description                |
| :------------------ | :------ | :------------------------- |
| network             | object  | Associated network object. |
| network.id          | integer | Network identifier.        |
| network.name        | string  | Network display name.      |
| network.description | string  | Network description.       |
