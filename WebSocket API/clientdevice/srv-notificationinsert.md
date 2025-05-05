---
title: "srv: notification/insert"
slug: "srv-notificationinsert"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Sat Jul 15 2017 13:16:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Notifies the user about new device notification.

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "subscriptionId": {guid},
    "notification": {
        "id": {integer},
        "notification": {string},
        "deviceId": {string},
        "timestamp": {datetime},
        "parameters": {object}
    }
}
```

**Message Parameters**

| Property Name             | Type     | Description                                                                             |
| :------------------------ | :------- | :-------------------------------------------------------------------------------------- |
| action                    | string   | Action name: notification/insert                                                        |
| subscriptionId            | guid     | Identifier of the associated subscription.                                              |
| notification              | object   | A  [DeviceNotification](doc:devicenotification) resource representing the notification. |
| notification.id           | integer  | Notification identifier.                                                                |
| notification.notification | string   | Notification name.                                                                      |
| notification.deviceId     | string   | Device unique identifier.                                                               |
| notification.timestamp    | datetime | Notification timestamp (UTC).                                                           |
| notification.parameters   | object   | Notification parameters, a JSON object with an arbitrary structure.                     |
