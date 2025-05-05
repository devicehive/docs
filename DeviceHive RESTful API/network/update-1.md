---
title: "update"
slug: "update-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 05 2017 06:43:55 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Updates an existing device network.

## Request

**HTTP Request**

```text
PUT /network/{id}
```

**Parameters**

Parameter Name	Required	Type	Description  
id	Yes	integer	Network identifier.  
**Authorization**

Access JSON Web Token (ManageNetwork)

**Request Body**

In the request body, supply a [Network](doc:network) resource.

| Property Name | Type    | Description           |
| :------------ | :------ | :-------------------- |
| id            | integer | Network identifier.   |
| name          | string  | Network display name. |
| description   | string  | Network description   |

## Response

If successful, this method returns an empty response body.
