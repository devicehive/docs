---
title: "notification/get"
slug: "notificationget-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:00:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:31:52 GMT+0000 (Coordinated Universal Time)"
---
Gets information about the notification.

**Authorization**

Access JSON Web Token (GetDeviceNotification)

## Request Topic and Payload

**Topic**

```text
dh/request
```

**Payload Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string},
    "notificationId": {long}
}
```

**Payload Parameters**

| Property Name  | Required | Type   | Description                                                             |
| :------------- | :------- | :----- | :---------------------------------------------------------------------- |
| action         | Yes      | string | Action name: notification/get                                           |
| requestId      | No       | object | Request unique identifier, will be passed back in the response message. |
| deviceId       | Yes      | string | Device unique identifier.                                               |
| notificationId | Yes      | long   | Notification unique identifier.                                         |

## Response Topic and Payload

**Topic**

```text
dh/response/notification/get@{clientId}
```

**Payload Representation**

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

**Payload Parameters**

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
