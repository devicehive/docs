---
title: "query"
slug: "query-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 14:28:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 15:30:52 GMT+0000 (Coordinated Universal Time)"
---
Queries device notifications.

## Request

**HTTP Request**

```text
GET /device/{deviceId}/notification
```

**Parameters**

| Parameter Name | Required | Type     | Description                                                                                                               |
| :------------- | :------- | :------- | :------------------------------------------------------------------------------------------------------------------------ |
| deviceId       | Yes      | string   | Device unique identifier.                                                                                                 |
| start          | No       | datetime | Filter by notification start UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| end            | No       | datetime | Filter by notification end UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)).   |
| notification   | No       | string   | Filter by notification name.                                                                                              |
| sortField      | No       | string   | Result list sort field. Available values are Timestamp (default) and Notification.                                        |
| sortOrder      | No       | string   | Result list sort order. Available values are ASC and DESC.                                                                |
| take           | No       | integer  | Number of records to take from the result list (default is 100).                                                          |
| skip           | No       | integer  | Number of records to skip from the result list.                                                                           |

**Authorization**

Access JSON Web Token (GetDeviceNotification)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns array of [DeviceNotification](doc:devicenotification)  resources in the response body.

| Property Name | Type     | Description                                                                                               |
| :------------ | :------- | :-------------------------------------------------------------------------------------------------------- |
| id            | integer  | Notification identifier                                                                                   |
| notification  | string   | Notification name.                                                                                        |
| deviceId      | string   | Device unique identifier.                                                                                 |
| networkId     | integer  | Network unique identifier.                                                                                |
| timestamp     | datetime | Notification UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| parameters    | object   | Notification parameters, a JSON object with an arbitrary structure.                                       |
