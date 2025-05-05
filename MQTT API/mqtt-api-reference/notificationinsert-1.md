---
title: "notification/insert"
slug: "notificationinsert-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:00:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:32:10 GMT+0000 (Coordinated Universal Time)"
---
Creates new device notification on behalf of device.

**Authorization**

Access JSON Web Token (CreateDeviceNotification)

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
    "notification": {
        "notification": {string},
        "timestamp": {datatime},
        "parameters": {object}
    }
}
```

**Payload Parameters**

| Property Name             | Required | Type     | Description                                                                                               |
| :------------------------ | :------- | :------- | :-------------------------------------------------------------------------------------------------------- |
| action                    | Yes      | string   | Action name: notification/insert                                                                          |
| requestId                 | No       | object   | Request unique identifier, will be passed back in the response message.                                   |
| deviceId                  | Yes      | string   | Device unique identifier.                                                                                 |
| notification              | Yes      | object   | A DeviceNotification resource to create.                                                                  |
| notification.notification | Yes      | string   | Notification name.                                                                                        |
| notification.timestamp    | No       | datetime | Notification UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| notification.parameters   | No       | object   | Notification parameters, a JSON object with an arbitrary structure.                                       |

## Response Topic and Payload

**Topic**

```text
dh/response/notification/insert@{clientId}
```

**Payload Representation**

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

**Payload Parameters**

| Property Name          | Type     | Description                                                                                                |
| :--------------------- | :------- | :--------------------------------------------------------------------------------------------------------- |
| action                 | string   | Action name: notification/insert                                                                           |
| status                 | string   | Operation execution status (success or error).                                                             |
| requestId              | object   | Request unique identifier as specified in the request message.                                             |
| notification           | object   | An inserted [DeviceNotification](doc:devicenotification)  resource.                                        |
| notification.id        | integer  | Notification identifier.                                                                                   |
| notification.timestamp | datetime | Notification UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601))). |
