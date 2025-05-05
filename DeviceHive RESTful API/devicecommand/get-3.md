---
title: "get"
slug: "get-3"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 11:16:55 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 15:33:30 GMT+0000 (Coordinated Universal Time)"
---
Gets information about device command.

## Request

**HTTP Request**

```text
GET /device/{deviceId}/command/{commandId}
```

**Parameters**

| Parameter Name | Required | Type    | Description               |
| :------------- | :------- | :------ | :------------------------ |
| deviceId       | Yes      | string  | Device unique identifier. |
| commandId      | Yes      | integer | Command identifier.       |

**Authorization**

Access JSON Web Token (GetDeviceCommand)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns a [DeviceCommand](doc:devicecommand) resource in the response body.

| Property Name | Type     | Description                                                                                                      |
| :------------ | :------- | :--------------------------------------------------------------------------------------------------------------- |
| id            | integer  | Command identifier.                                                                                              |
| command       | string   | Command name                                                                                                     |
| timestamp     | datetime | Command UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)).             |
| lastUpdated   | datetime | Last command update UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| userId        | integer  | Associated user identifier.                                                                                      |
| deviceId      | string   | Device unique identifier.                                                                                        |
| networkId     | integer  | Network unique identifier.                                                                                       |
| parameters    | object   | Command parameters, a JSON object with an arbitrary structure.                                                   |
| lifetime      | integer  | Command lifetime, a number of seconds until this command expires.                                                |
| status        | string   | Command status, as reported by device or related infrastructure.                                                 |
| result        | object   | Command execution result, an optional value that could be provided by device                                     |
