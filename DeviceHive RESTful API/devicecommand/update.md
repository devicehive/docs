---
title: "update"
slug: "update"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 11:17:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Apr 19 2018 08:32:51 GMT+0000 (Coordinated Universal Time)"
---
Updates an existing device command.

## Request

**HTTP Request**

```text
PUT /device/{deviceId}/command/{commandId}
```

**Parameters**

| Parameter Name | Required | Type    | Description                |
| :------------- | :------- | :------ | :------------------------- |
| deviceId       | Yes      | string  | Device unique identifier.  |
| commandId      | Yes      | integer | Device command identifier. |

**Authorization**

Access JSON Web Token (UpdateDeviceCommand)

**Request Body**

In the request body, supply a [DeviceCommand](doc:devicecommand)  resource.

| Property Name | Required | Type   | Description                                                                   |
| :------------ | :------- | :----- | :---------------------------------------------------------------------------- |
| status        | No       | string | Command status, as reported by device or related infrastructure.              |
| result        | No       | object | Command execution result, an optional value that could be provided by device. |

## Response

If successful, this method returns an empty response body.
