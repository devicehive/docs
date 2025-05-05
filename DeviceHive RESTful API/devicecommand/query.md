---
title: "query"
slug: "query"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 11:16:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 15:31:24 GMT+0000 (Coordinated Universal Time)"
---
Queries device commands.

## Request

**HTTP Request**

```text
GET /device/{deviceId}/command
```

**Parameters**

| Parameter Name | Required | Type     | Description                                                                                                          |
| :------------- | :------- | :------- | :------------------------------------------------------------------------------------------------------------------- |
| deviceId       | Yes      | string   | Device unique identifier.                                                                                            |
| start          | No       | datetime | Filter by command start UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| end            | No       | datetime | Filter by command end UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)).   |
| command        | No       | string   | Filter by command name.                                                                                              |
| status         | No       | string   | Filter by command status.                                                                                            |
| sortField      | No       | string   | Result list sort field. Available values are Timestamp (default), Command and Status.                                |
| sortOrder      | No       | string   | Result list sort order. Available values are ASC and DESC.                                                           |
| take           | No       | integer  | Number of records to take from the result list (default is 1000).                                                    |
| skip           | No       | integer  | Number of records to skip from the result list.                                                                      |

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
| parameters    | object   | Command parameters, a JSON object with an arbitrary structure.                                                   |
| lifetime      | integer  | Command lifetime, a number of seconds until this command expires.                                                |
| status        | string   | Command status, as reported by device or related infrastructure.                                                 |
| result        | object   | Command execution result, an optional value that could be provided by device.                                    |
