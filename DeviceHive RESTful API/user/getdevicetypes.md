---
title: "getDeviceTypes"
slug: "getdevicetypes"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed May 23 2018 11:41:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets information about all user/device type associations.

## Request

**HTTP Request**

```text
GET /user/{id}/devicetype
```

**Parameters**

| Parameter Name | Required | Type    | Description      |
| :------------- | :------- | :------ | :--------------- |
| id             | Yes      | integer | User identifier. |

**Authorization**

Access JSON Web Token (ManageUser)

**Request Body**

In the request body, supply the empty object.

## Response

If successful, this method returns array of [DeviceType](doc:devicetype) resources in the response body.

| Property Name | Type    | Description              |
| :------------ | :------ | :----------------------- |
| id            | integer | Device type identifier.  |
| name          | string  | Device type name.        |
| description   | string  | Device type description. |
