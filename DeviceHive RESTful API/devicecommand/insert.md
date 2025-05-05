---
title: "insert"
slug: "insert"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 11:17:02 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 15:04:28 GMT+0000 (Coordinated Universal Time)"
---
Creates new device command.

## Request

**HTTP Request**

```text
POST /device/{deviceId}/command
```

**Parameters**

| Parameter Name | Required | Type   | Description               |
| :------------- | :------- | :----- | :------------------------ |
| deviceId       | Yes      | string | Device unique identifier. |

**Authorization**

Access JSON Web Token (CreateDeviceCommand)

**Request Body**

In the request body, supply a [DeviceCommand](doc:devicecommand) resource.

| Property Name | Required | Type     | Description                                                                                          |
| :------------ | :------- | :------- | :--------------------------------------------------------------------------------------------------- |
| command       | Yes      | string   | Command name.                                                                                        |
| timestamp     | No       | datetime | Command UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| parameters    | No       | object   | Command parameters, a JSON object with an arbitrary structure.                                       |
| lifetime      | No       | integer  | Command lifetime, a number of seconds until this command expires.                                    |
| status        | No       | string   | Command status, as reported by device or related infrastructure.                                     |
| result        | No       | object   | Command execution result, an optional value that could be provided by device.                        |

## Response

If successful, this method returns a [DeviceCommand](doc:devicecommand) resource in the response body.

| Property Name | Type     | Description                                                                                                      |
| :------------ | :------- | :--------------------------------------------------------------------------------------------------------------- |
| id            | integer  | Command identifier.                                                                                              |
| timestamp     | datetime | Command UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)).             |
| lastUpdated   | datetime | Last command update UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| userId        | integer  | Associated user identifier.                                                                                      |
