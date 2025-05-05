---
title: "update"
slug: "update-3"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 10 2018 13:52:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Updates an existing device type.

## Request

**HTTP Request**

```text
PUT /devicetype/{id}
```

**Parameters**

| Parameter Name | Required | Type    | Description             |
| :------------- | :------- | :------ | :---------------------- |
| id             | Yes      | integer | Device type identifier. |

**Authorization**

Access JSON Web Token (ManageDeviceType)

**Request Body**

In the request body, supply a [DeviceType](doc:devicetype) resource.

| Property Name | Type   | Description              |
| :------------ | :----- | :----------------------- |
| name          | string | Device type name.        |
| description   | string | Device type description. |

## Response

If successful, this method returns an empty response body.
