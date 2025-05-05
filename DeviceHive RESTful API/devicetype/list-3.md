---
title: "list"
slug: "list-3"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 10 2018 12:55:05 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets list of device types.

The result list is limited to device types the client has access to.

## Request

**HTTP Request**

```text
GET /devicetype
```

**Parameters**

| Parameter Name | Required | Type    | Description                                                                        |
| :------------- | :------- | :------ | :--------------------------------------------------------------------------------- |
| name           | No       | string  | Filter by device type name.                                                        |
| namePattern    | No       | string  | Filter by device type name pattern. In pattern wildcards '%' and '\_' can be used. |
| sortField      | No       | string  | Result list sort field. Available values are ID and Name.                          |
| sortOrder      | No       | string  | Result list sort order. Available values are ASC and DESC.                         |
| take           | No       | integer | Number of records to take from the result list.                                    |
| skip           | No       | integer | Number of records to skip from the result list.                                    |

**Authorization**

Access JSON Web Token (GetDeviceType)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns array of [DeviceType](doc:devicetype) resources in the response body.

| Property Name | Type    | Description              |
| :------------ | :------ | :----------------------- |
| id            | integer | Device type identifier.  |
| name          | string  | Device type name.        |
| description   | string  | Device type description. |
