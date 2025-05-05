---
title: "pollMany"
slug: "pollmany"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 11:17:34 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Jan 22 2018 16:04:55 GMT+0000 (Coordinated Universal Time)"
---
Polls new device commands.

This method returns all device commands that were created after specified timestamp.

In the case when no commands were found, the method blocks until new command is received. If no commands are received within the waitTimeout period, the server returns an empty response. In this case, to continue polling, the client should repeat the call with the same timestamp value.

## Request

**HTTP Request**

```text
GET /device/command/poll?deviceId={deviceId}&networkIds={networkIds}&deviceTypeIds={deviceTypeIds}&timestamp={timestamp}&names={names}&waitTimeout={waitTimeout}
```

**Parameters**

| Parameter Name | Required | Type     |                                                                                                                                                                                      |
| :------------- | :------- | :------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| deviceId       | No       | string   | Device unique identifier.                                                                                                                                                            |
| networkIds     | No       | string   | Comma-separated list of network unique identifiers.                                                                                                                                  |
| deviceTypeIds  | No       | string   | Comma-separated list of device type unique identifiers.                                                                                                                              |
| timestamp      | No       | datetime | UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)) of the last received command. If not specified, the server's timestamp is taken instead. |
| names          | No       | string   | Comma-separated list of commands names.                                                                                                                                              |
| waitTimeout    | No       | integer  | Waiting timeout in seconds (default: 30 seconds, maximum: 60 seconds). Specify 0 to disable waiting.                                                                                 |
| limit          | No       | integer  | Limits number of commands.                                                                                                                                                           |

**Authorization**

Access JSON Web Token (GetDeviceCommand)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns array of the following resources in the response body.

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
