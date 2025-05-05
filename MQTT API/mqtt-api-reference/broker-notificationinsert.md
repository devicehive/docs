---
title: "broker: notification/insert"
slug: "broker-notificationinsert"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:04:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:58:15 GMT+0000 (Coordinated Universal Time)"
---
Notifies the user about new device notification.

## Subscription Topic and Payload

**Topic**

```text
dh/notification/{network-id}/{devicetype-id}/{device-id}/{notification-name}
```

Where:

- network-id - DeviceHive Network ID
- devicetype-id - DeviceHive DeviceType ID
- device-id - DeviceHive Device ID
- notification-name - Notification name

**Payload Representation**

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

**Payload Parameters**

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
