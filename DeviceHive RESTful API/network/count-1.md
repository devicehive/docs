---
title: "count"
slug: "count-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jan 09 2018 13:24:56 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jan 09 2018 14:47:59 GMT+0000 (Coordinated Universal Time)"
---
Gets count of networks.

## Request

**HTTP Request**

```text
GET /network/count
```

**Parameters**

| Parameter Name | Required | Type   | Description                     |
| :------------- | :------- | :----- | :------------------------------ |
| name           | No       | string | Filter by network name.         |
| namePattern    | No       | string | Filter by network name pattern. |

**Authorization**

Access JSON Web Token (GetNetwork)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns the count of [Network](doc:network) resources in the response body.

| Property Name | Type    | Description                                |
| :------------ | :------ | :----------------------------------------- |
| count         | integer | Number of networks that match the filters. |
