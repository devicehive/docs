---
title: "poll"
slug: "poll"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 11:17:18 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Jan 22 2018 15:58:34 GMT+0000 (Coordinated Universal Time)"
---
Polls new device commands.

This method returns all device commands that were created after specified timestamp.

In the case when no commands were found, the method blocks until new command is received. If no commands are received within the waitTimeout period, the server returns an empty response. In this case, to continue polling, the client should repeat the call with the same timestamp value.

## Request

**HTTP Request**

```text
GET /device/{deviceId}/command/poll?timestamp={timestamp}&names={names}&waitTimeout={waitTimeout}
```

**Parameters**

| Parameter Name        | Required | Type     | Description                                                                                                                                                                                                                             |
| :-------------------- | :------- | :------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| deviceId              | Yes      | string   | Device unique identifier.                                                                                                                                                                                                               |
| timestamp             | No       | datetime | UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)) of the last received  / last updated (if returnUpdatedCommands selected) command. If not specified, the server's datetime is taken instead. |
| returnUpdatedCommands | No       | boolean  | Checks if updated commands should be returned. If not specified, default value is false.                                                                                                                                                |
| names                 | No       | string   | Comma-separated list of commands names.                                                                                                                                                                                                 |
| waitTimeout           | No       | long     | Waiting timeout in seconds (default: 30 seconds, maximum: 60 seconds). Specify 0 to disable waiting.                                                                                                                                    |
| limit                 | No       | integer  | Limits number of commands.                                                                                                                                                                                                              |

**Authorization**

Access JSON Web Token (GetDeviceCommand)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns array of [DeviceCommand](doc:devicecommand) resources in the response body.

| Property Name | Type     | Description                                                                                                      |
| :------------ | :------- | :--------------------------------------------------------------------------------------------------------------- |
| id            | integer  | Command identifier.                                                                                              |
| command       | string   | Command name                                                                                                     |
| timestamp     | datetime | Command UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)).             |
| lastUpdated   | datetime | Last command update UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| userId        | integer  | Associated user identifier.                                                                                      |
| deviceId      | string   | Device unique identifier.                                                                                        |
| networkId     | integer  | Network unique identifier.                                                                                       |
| deviceTypeId  | integer  | Device type unique identifier.                                                                                   |
| parameters    | object   | Command parameters, a JSON object with an arbitrary structure.                                                   |
| lifetime      | integer  | Command lifetime, a number of seconds until this command expires.                                                |
| status        | string   | Command status, as reported by device or related infrastructure.                                                 |
| result        | object   | Command execution result, an optional value that could be provided by device                                     |
