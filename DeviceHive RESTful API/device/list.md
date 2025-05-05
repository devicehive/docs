---
title: "list"
slug: "list"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 09:58:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets list of devices.

## Request

**HTTP Request**

```text
GET /device
```

**Parameters**

| Parameter Name | Required | Type    | Description                                                                         |
| :------------- | :------- | :------ | :---------------------------------------------------------------------------------- |
| name           | No       | string  | Filter by device name.                                                              |
| namePattern    | No       | string  | Filter by device name pattern.                                                      |
| networkId      | No       | long    | Filter by associated network identifier.                                            |
| networkName    | No       | string  | Filter by associated network name.                                                  |
| sortField      | No       | string  | Result list sort field. Available values are Name, Status, Network and DeviceClass. |
| sortOrder      | No       | string  | Available values are ASC and DESC.                                                  |
| take           | No       | integer | Number of records to take from the result list.                                     |
| skip           | No       | integer | Number of records to skip from the result list.                                     |

**Authorization**

Access JSON Web Token (GetDevice)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns array of [Device](doc:device) resources in the response body.

| Property Name | Type    | Description                                             |
| :------------ | :------ | :------------------------------------------------------ |
| id            | string  | Device unique identifier.                               |
| name          | string  | Device display name.                                    |
| data          | object  | Device data, a JSON object with an arbitrary structure. |
| networkId     | integer | Associated network id.                                  |
| isBlocked     | boolean | Indicates whether device is blocked.                    |
