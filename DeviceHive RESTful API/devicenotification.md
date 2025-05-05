---
title: "DeviceNotification"
slug: "devicenotification"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 12:30:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Jan 22 2018 16:08:16 GMT+0000 (Coordinated Universal Time)"
---
Represents a device notification, a unit of information dispatched from devices.

## Methods

[block:parameters]
{
  "data": {
    "h-0": "Method",
    "h-1": "Authorization",
    "h-2": "Uri",
    "h-3": "Description",
    "0-0": "[query](doc:query-1)",
    "0-1": "Access JSON Web Token (GetDeviceNotification)",
    "0-2": "GET /device/{deviceId}/notification",
    "0-3": "Queries device notifications.",
    "1-0": "[get](doc:get-4)",
    "1-1": "Access JSON Web Token (GetDeviceNotification)",
    "1-2": "GET /device/{deviceId}/notification/{id}",
    "1-3": "Gets information about device notification.",
    "2-0": "[insert](doc:insert-1)",
    "2-1": "Access JSON Web Token (CreateDeviceNotification)",
    "2-2": "POST /device/{deviceId}/notification",
    "2-3": "Creates new device notification.",
    "3-0": "[poll](doc:poll-1)",
    "3-1": "Access JSON Web Token (GetDeviceNotification)",
    "3-2": "GET /device/{deviceId}/notification/poll",
    "3-3": "Polls new device notifications.  \nThis method returns all device notifications that were created after specified timestamp.  \nIn the case when no notifications were found, the method blocks until new notification is received. If no notifications are received within the waitTimeout period, the server returns an empty response. In this case, to continue polling, the client should repeat the call with the same timestamp value.",
    "4-0": "[pollMany](doc:pollmany-1)",
    "4-1": "Access JSON Web Token (GetDeviceNotification)",
    "4-2": "GET /device/notification/poll",
    "4-3": "Polls new device notifications.  \nThis method returns all device notifications that were created after specified timestamp.  \nIn the case when no notifications were found, the method blocks until new notification is received. If no notifications are received within the waitTimeout period, the server returns an empty response. In this case, to continue polling, the client should repeat the call with the same timestamp value."
  },
  "cols": 4,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Resource Representation

```text
{
    "id": {integer},
    "notification": {string},
    "deviceId": {string},
    "networkId": {integer},
    "deviceTypeId": {integer},
    "timestamp": {datetime},
    "parameters": {object}
}
```

| Property Name | Type     | Description                                                                                               |
| :------------ | :------- | :-------------------------------------------------------------------------------------------------------- |
| id            | integer  | Notification identifier.                                                                                  |
| notification  | string   | Notification name.                                                                                        |
| deviceId      | string   | Device unique identifier.                                                                                 |
| networkId     | integer  | Network unique identifier.                                                                                |
| deviceTypeId  | integer  | Device type unique identifier.                                                                            |
| timestamp     | datetime | Notification UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| parameters    | object   | Notification parameters, a JSON object with an arbitrary structure.                                       |
