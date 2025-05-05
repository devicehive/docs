---
title: "get"
slug: "get-5"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 05 2017 06:43:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets information about device network and its devices.

## Request

**HTTP Request**

```text
GET /network/{id}
```

**Parameters**

| Parameter Name | Required | Type    | Description        |
| :------------- | :------- | :------ | :----------------- |
| id             | Yes      | integer | Network identifier |

**Authorization**

Access JSON Web Token (GetNetwork)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns a [Network](doc:network)  resource in the response body.

| Property Name | Type    | Description           |
| :------------ | :------ | :-------------------- |
| id            | integer | Network identifier.   |
| name          | string  | Network display name. |
| description   | string  | Network description   |
