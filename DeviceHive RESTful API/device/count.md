---
title: "count"
slug: "count"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jan 09 2018 12:52:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jan 09 2018 14:27:33 GMT+0000 (Coordinated Universal Time)"
---
Gets count of devices.

## Request

**HTTP Request**

```text
GET /device/count
```

**Parameters**

| Parameter Name | Required | Type   | Description                              |
| :------------- | :------- | :----- | :--------------------------------------- |
| name           | No       | string | Filter by device name.                   |
| namePattern    | No       | string | Filter by device name pattern.           |
| networkId      | No       | long   | Filter by associated network identifier. |
| networkName    | No       | string | Filter by associated network name.       |

**Authorization**

Access JSON Web Token (GetDevice)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns the count of [Device](doc:device) resources in the response body.

| Property Name | Type    | Description                               |
| :------------ | :------ | :---------------------------------------- |
| count         | integer | Number of devices that match the filters. |
