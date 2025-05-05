---
title: "insert"
slug: "insert-4"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 10 2018 13:44:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Creates new device type.

## Request

**HTTP Request**

```text
POST /devicetype
```

**Authorization**

Access JSON Web Token (ManageDeviceType)

**Request Body**

In the request body, supply a [DeviceType](doc:devicetype) resource.

| Property Name | Required | Type   | Description              |
| :------------ | :------- | :----- | :----------------------- |
| name          | Yes      | string | Device type name.        |
| description   | No       | string | Device type description. |

## Response

If successful, this method returns a device type identifier in the response body. 

| Property Name | Type    | Description             |
| :------------ | :------ | :---------------------- |
| id            | integer | Device type identifier. |
