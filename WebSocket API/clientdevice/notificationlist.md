---
title: "notification/list"
slug: "notificationlist"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Sat Jul 15 2017 08:16:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 23:38:08 GMT+0000 (Coordinated Universal Time)"
---
Gets the list of notifications for device.

## Request Message

**Authorization**

Access JSON Web Token (GetDeviceNotification)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string},
    "start": {datetime},
    "end": {datetime},
    "notification": {string},
    "sortField": {string},
    "sortOrder": {string},
    "take": {integer},
    "skip": {integer}
}
```

**Message Parameters**

| Property Name | Required | Type     | Description                                                                                                                |
| :------------ | :------- | :------- | :------------------------------------------------------------------------------------------------------------------------- |
| action        | Yes      | string   | Action name: notification/list                                                                                             |
| requestId     | No       | object   | Request unique identifier, will be passed back in the response message.                                                    |
| deviceId      | Yes      | string   | Device unique identifier.                                                                                                  |
| start         | No       | datetime | Start UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)) to filter notifications. |
| end           | No       | datetime | End UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)) to filter notifications.   |
| notification  | No       | string   | Filter by command name.                                                                                                    |
| sortField     | No       | string   | Result list sort field.                                                                                                    |
| sortOrder     | No       | string   | Result list sort order. Available values are ASC and DESC. The sortField should be specified.                              |
| take          | No       | integer  | Number of records to take from the result list. If not specified 100 records will be taken.                                |
| skip          | No       | integer  | Number of records to skip from the result list. If not specified 0 records will be skipped.                                |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "status": {string},
    "notifications": [{
        "id": {long},
        "notification": {string},
        "timestamp": {datetime},
        "deviceId": {string},
        "networkId": {integer},
        "parameters": {object}
    }]

}
```

**Message Parameters**

| Property Name             | Type     | Description                                                                                               |
| :------------------------ | :------- | :-------------------------------------------------------------------------------------------------------- |
| action                    | string   | Action name: notification/list                                                                            |
| requestId                 | object   | Request unique identifier as specified in the request message.                                            |
| status                    | string   | Operation execution status (success or error).                                                            |
| notifications             | array    | The array of notifications.                                                                               |
| notification              | object   | An inserted [DeviceNotification](doc:devicenotification)  resource.                                       |
| notification.id           | long     | Notification identifier.                                                                                  |
| notification.notification | string   | Notification name.                                                                                        |
| notification.timestamp    | datetime | Notification UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| notification.deviceId     | string   | Associated device identifier.                                                                             |
| notification.networkId    | integer  | Associated network identifier.                                                                            |
| notification.parameters   | object   | Notification parameters, a JSON object with an arbitrary structure.                                       |
