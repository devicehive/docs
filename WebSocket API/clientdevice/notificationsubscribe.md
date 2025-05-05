---
title: "notification/subscribe"
slug: "notificationsubscribe"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Sat Jul 15 2017 08:17:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Jan 22 2018 16:09:40 GMT+0000 (Coordinated Universal Time)"
---
Subscribes to device notifications. After subscription is completed, the server will start to send notification/insert messages to the connected user.

## Request Message

**Authorization**

Access JSON Web Token (GetDeviceNotification)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "timestamp": {datetime},
    "deviceId": {string},
    "networkIds": {array},
    "deviceTypeIds": {array},
    "names": {array}
}
```

**Message Parameters**

| Property Name | Required | Type     | Description                                                                                                                                                                               |
| :------------ | :------- | :------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| action        | Yes      | string   | Action name: notification/subscribe                                                                                                                                                       |
| requestId     | No       | object   | Request unique identifier, will be passed back in the response message.                                                                                                                   |
| timestamp     | No       | datetime | UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)) of the last received notification. If not specified, the server's timestamp is taken instead. |
| deviceId      | No       | string   | A unique device identifier to subscribe to. If not specified, the subscription is made to all accessible devices.                                                                         |
| networkIds    | No       | array    | Array of network unique identifiers to subscribe to.                                                                                                                                      |
| deviceTypeIds | No       | array    | Array of device type unique identifiers to subscribe to.                                                                                                                                  |
| names         | No       | array    | Array of notification names to subscribe to.                                                                                                                                              |

## Response Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "subscriptionId": {integer}
}
```

**Message Parameters**

| Property Name  | Type    | Description                                                    |
| :------------- | :------ | :------------------------------------------------------------- |
| action         | string  | Action name: notification/subscribe                            |
| status         | string  | Operation execution status (success or error).                 |
| requestId      | object  | Request unique identifier as specified in the request message. |
| subscriptionId | integer | A unique identifier of the subscription made.                  |
