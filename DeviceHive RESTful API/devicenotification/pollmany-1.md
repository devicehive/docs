---
title: "pollMany"
slug: "pollmany-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 14:29:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Jan 22 2018 16:04:32 GMT+0000 (Coordinated Universal Time)"
---
Polls new device notifications.

This method returns all device notifications that were created after specified timestamp.

In the case when no notifications were found, the method blocks until new notification is received. If no notifications are received within the waitTimeout period, the server returns an empty response. In this case, to continue polling, the client should repeat the call with the same timestamp value.

## Request

**HTTP Request**

```text
GET /device/notification/poll?deviceId={deviceId}&networkIds={networkIds}&deviceTypeIds={deviceTypeIds}&timestamp={timestamp}&names={names}&waitTimeout={waitTimeout}
```

**Parameters**

| Parameter Name | Required | Type     | Description                                                                                                   |
| :------------- | :------- | :------- | :------------------------------------------------------------------------------------------------------------ |
| deviceId       | No       | string   | Device unique identifier.                                                                                     |
| networkIds     | No       | string   | Comma-separated list of network unique identifiers.                                                           |
| deviceTypeId   | No       | string   | Comma-separated list of device type unique identifiers.                                                       |
| timestamp      | No       | datetime | Timestamp of the last received notification (UTC). If not specified, the server's timestamp is taken instead. |
| names          | No       | string   | Comma-separated list of notification names.                                                                   |
| waitTimeout    | No       | long     | Waiting timeout in seconds (default: 30 seconds, maximum: 60 seconds). Specify 0 to disable waiting.          |

**Authorization**

Access JSON Web Token (GetDeviceNotification)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns array of the following resources in the response body.

| Property Name | Type     | Description                                                                                               |
| :------------ | :------- | :-------------------------------------------------------------------------------------------------------- |
| id            | integer  | Notification identifier.                                                                                  |
| notification  | string   | Notification name.                                                                                        |
| deviceId      | string   | Device unique identifier.                                                                                 |
| networkId     | integer  | Network unique identifier.                                                                                |
| deviceTypeId  | integer  | Device type unique identifier.                                                                            |
| timestamp     | datetime | Notification UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| parameters    | object   | Notification parameters, a JSON object with an arbitrary structure.                                       |
