---
title: "get"
slug: "get-7"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 10 2018 13:16:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jan 10 2018 14:47:49 GMT+0000 (Coordinated Universal Time)"
---
Gets information about device type and its devices.

## Request

**HTTP Request**

```text
GET /devicetype/{id}
```

**Parameters**

| Parameter Name | Required | Type    | Description             |
| :------------- | :------- | :------ | :---------------------- |
| id             | Yes      | integer | Device type identifier. |

**Authorization**

Access JSON Web Token (GetDeviceType)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns a [DeviceType](doc:devicetype) resource with the list of [Devices](doc:device) in the response body.

| Property Name       | Type    | Description                                             |
| :------------------ | :------ | :------------------------------------------------------ |
| id                  | integer | Device type identifier.                                 |
| name                | string  | Device type name.                                       |
| description         | string  | Device type description.                                |
| device              | object  | The [Device](doc:device) resource.                      |
| device.id           | string  | Device unique identifier.                               |
| device.name         | string  | Device display name.                                    |
| device.data         | object  | Device data, a JSON object with an arbitrary structure. |
| device.networkId    | integer | Associated network id.                                  |
| device.deviceTypeId | integer | Associated device type id.                              |
| device.isBlocked    | boolean | Indicates whether device is blocked.                    |
