---
title: "notification/get"
slug: "notificationget"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Sat Jul 15 2017 08:16:18 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 23:34:49 GMT+0000 (Coordinated Universal Time)"
---
Gets information about the notification.

## Request Message

**Authorization**

Access JSON Web Token (GetDeviceNotification)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string},
    "notificationId": {long}
}
```

**Message Parameters**

| Property Name  | Required | Type   | Description                                                             |
| :------------- | :------- | :----- | :---------------------------------------------------------------------- |
| action         | Yes      | string | Action name: notification/get                                           |
| requestId      | No       | object | Request unique identifier, will be passed back in the response message. |
| deviceId       | Yes      | string | Device unique identifier.                                               |
| notificationId | Yes      | long   | Notification unique identifier.                                         |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "notification": {
        "id": {long},
        "notification": {string},
        "timestamp": {datetime},
        "deviceId": {string},
        "networkId": {integer},
        "parameters": {object}
    }
}
```

**Message Parameters**

| Property Name             | Type     | Description                                                                                               |
| :------------------------ | :------- | :-------------------------------------------------------------------------------------------------------- |
| action                    | string   | Action name: notification/get                                                                             |
| status                    | string   | Operation execution status (success or error).                                                            |
| requestId                 | object   | Request unique identifier as specified in the request message.                                            |
| notification              | object   | An inserted [DeviceNotification](doc:devicenotification) resource.                                        |
| notification.id           | long     | Notification identifier.                                                                                  |
| notification.notification | string   | Notification name.                                                                                        |
| notification.timestamp    | datetime | Notification UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| notification.deviceId     | string   | Associated device identifier.                                                                             |
| notification.networkId    | integer  | Associated network identifier.                                                                            |
| notification.parameters   | object   | Notification parameters, a JSON object with an arbitrary structure.                                       |
