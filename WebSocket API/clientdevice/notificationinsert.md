---
title: "notification/insert"
slug: "notificationinsert"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Sat Jul 15 2017 08:16:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 23:39:10 GMT+0000 (Coordinated Universal Time)"
---
Creates new device notification on behalf of device.

## Request Message

**Authorization**

Access JSON Web Token (CreateDeviceNotification)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string},
    "notification": {
        "notification": {string},
        "timestamp": {datatime},
        "parameters": {object}
    }
}
```

**Message Parameters**

| Property Name             | Required | Type     | Description                                                                                               |
| :------------------------ | :------- | :------- | :-------------------------------------------------------------------------------------------------------- |
| action                    | Yes      | string   | Action name: notification/insert                                                                          |
| requestId                 | No       | object   | Request unique identifier, will be passed back in the response message.                                   |
| deviceId                  | Yes      | string   | Device unique identifier.                                                                                 |
| notification              | Yes      | object   | A DeviceNotification resource to create.                                                                  |
| notification.notification | Yes      | string   | Notification name.                                                                                        |
| notification.timestamp    | No       | datetime | Notification UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| notification.parameters   | No       | object   | Notification parameters, a JSON object with an arbitrary structure.                                       |

## Response Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "notification": {
        "id": {integer},
        "timestamp": {datetime}
    }
}
```

**Message Parameters**

| Property Name          | Type     | Description                                                                                                |
| :--------------------- | :------- | :--------------------------------------------------------------------------------------------------------- |
| action                 | string   | Action name: notification/insert                                                                           |
| status                 | string   | Operation execution status (success or error).                                                             |
| requestId              | object   | Request unique identifier as specified in the request message.                                             |
| notification           | object   | An inserted [DeviceNotification](doc:devicenotification)  resource.                                        |
| notification.id        | integer  | Notification identifier.                                                                                   |
| notification.timestamp | datetime | Notification UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601))). |
