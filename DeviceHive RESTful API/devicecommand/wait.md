---
title: "wait"
slug: "wait"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 11:17:26 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Jan 22 2018 15:59:06 GMT+0000 (Coordinated Universal Time)"
---
Waits for a command to be processed.

This method returns a command only if it has been processed by a device.

In the case when command is not processed, the method blocks until device acknowledges command execution. If the command is not processed within the waitTimeout period, the server returns an empty response. In this case, to continue polling, the client should repeat the call.

## Request

**HTTP Request**

```text
GET /device/{deviceId}/command/{commandId}/poll?waitTimeout={waitTimeout}
```

**Parameters**

|             |     |         |                                                                                                      |
| :---------- | :-- | :------ | :--------------------------------------------------------------------------------------------------- |
| deviceId    | Yes | string  | Device unique identifier.                                                                            |
| commandId   | Yes | integer | Command identifier.                                                                                  |
| waitTimeout | No  | integer | Waiting timeout in seconds (default: 30 seconds, maximum: 60 seconds). Specify 0 to disable waiting. |

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
| userId        | integer  | Associated user identifier.                                                                                      |
| deviceId      | string   | Device unique identifier.                                                                                        |
| networkId     | integer  | Network unique identifier.                                                                                       |
| deviceTypeId  | integer  | Device type unique identifier.                                                                                   |
| parameters    | object   | Command parameters, a JSON object with an arbitrary structure.                                                   |
| lifetime      | integer  | Command lifetime, a number of seconds until this command expires.                                                |
| status        | string   | Command status, as reported by device or related infrastructure.                                                 |
| result        | object   | Command execution result, an optional value that could be provided by device                                     |
| lastUpdated   | datetime | Last command update UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
