---
title: "notification/subscribe"
slug: "notificationsubscribe-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:01:17 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:32:23 GMT+0000 (Coordinated Universal Time)"
---
Subscribes to device notifications. After subscription is completed, the server will start to send notification/insert messages to the connected user.

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
    "timestamp": {datetime},
    "deviceId": {string},
    "networkIds": {array},
    "deviceTypeIds": {array},
    "names": {array}
}
```

**Payload Parameters**

| Property Name | Required | Type     | Description                                                                                                                                                                               |
| :------------ | :------- | :------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| action        | Yes      | string   | Action name: notification/subscribe                                                                                                                                                       |
| requestId     | No       | object   | Request unique identifier, will be passed back in the response message.                                                                                                                   |
| timestamp     | No       | datetime | UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)) of the last received notification. If not specified, the server's timestamp is taken instead. |
| deviceId      | No       | string   | A unique device identifier to subscribe to. If not specified, the subscription is made to all accessible devices.                                                                         |
| networkIds    | No       | array    | Array of network unique identifiers to subscribe to.                                                                                                                                      |
| deviceTypeIds | No       | array    | Array of device type unique identifiers to subscribe to.                                                                                                                                  |
| names         | No       | array    | Array of notification names to subscribe to.                                                                                                                                              |

## Response Topic and Payload

**Topic**

```text
dh/response/notification/subscribe@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "subscriptionId": {integer}
}
```

**Payload Parameters**

| Property Name  | Type    | Description                                                    |
| :------------- | :------ | :------------------------------------------------------------- |
| action         | string  | Action name: notification/subscribe                            |
| status         | string  | Operation execution status (success or error).                 |
| requestId      | object  | Request unique identifier as specified in the request message. |
| subscriptionId | integer | A unique identifier of the subscription made.                  |
