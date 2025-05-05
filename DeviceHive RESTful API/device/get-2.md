---
title: "get"
slug: "get-2"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 09:58:50 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets information about device.

## Request

**HTTP Request**

```text
GET /device/{id}
```

**Parameters**

| Parameter Name | Required | Type   | Description               |
| :------------- | :------- | :----- | :------------------------ |
| id             | Yes      | string | Device unique identifier. |

**Authorization**

Access JSON Web Token (GetDevice)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns a [Device](doc:device) resource in the response body.

| Property Name | Type    | Description                                             |
| :------------ | :------ | :------------------------------------------------------ |
| id            | string  | Device unique identifier.                               |
| name          | string  | Device display name.                                    |
| data object   | object  | Device data, a JSON object with an arbitrary structure. |
| networkId     | integer | Associated network id.                                  |
| isBlocked     | boolean | Indicates whether device is blocked.                    |
