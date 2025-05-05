---
title: "count"
slug: "count-3"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 10 2018 13:07:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets count of device types the client has access to.

## Request

**HTTP Request**

```text
GET /devicetype/count
```

**Parameters**

| Parameter Name | Required | Type   | Description                                                                        |
| :------------- | :------- | :----- | :--------------------------------------------------------------------------------- |
| name           | No       | string | Filter by device type name.                                                        |
| namePattern    | No       | string | Filter by device type name pattern. In pattern wildcards '%' and '\_' can be used. |

**Authorization**

Access JSON Web Token (GetDeviceType)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns the count of [DeviceType](doc:devicetype) resources in the response body.

| Property Name | Type    | Description                                    |
| :------------ | :------ | :--------------------------------------------- |
| count         | integer | Number of device types that match the filters. |
