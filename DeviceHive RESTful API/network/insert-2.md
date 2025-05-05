---
title: "insert"
slug: "insert-2"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 05 2017 06:43:45 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Oct 19 2017 07:13:33 GMT+0000 (Coordinated Universal Time)"
---
Creates new device network.

## Request

**HTTP Request**

```text
POST /network
```

**Authorization**

Access JSON Web Token (ManageNetwork)

**Request Body**

In the request body, supply a [Network](doc:network) resource.

| Property Name | Required | Type   | Description           |
| :------------ | :------- | :----- | :-------------------- |
| name          | Yes      | string | Network display name. |
| description   | No       | string | Network description   |

## Response

If successful, this method returns a network identifier in the response body. 

| Property Name | Type    | Description         |
| :------------ | :------ | :------------------ |
| id            | integer | Network identifier. |
