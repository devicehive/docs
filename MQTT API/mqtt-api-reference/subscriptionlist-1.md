---
title: "subscription/list"
slug: "subscriptionlist-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:01:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:32:46 GMT+0000 (Coordinated Universal Time)"
---
Get list of user subscriptions.

**Authorization**

Access JSON Web Token (GetDeviceCommand or GetDeviceNotification)

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
    "type": {string}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                                   |
| :------------ | :------- | :----- | :---------------------------------------------------------------------------- |
| action        | Yes      | string | Action name: subscription/list                                                |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message.       |
| type          | No       | string | Type of returned subscriptions, possible values: 'command' or 'notification'. |

## Response Topic and Payload

**Topic**

```text
dh/response/subscription/list@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "subscriptions": [{
        "subscriptionId": {integer},
        "type": {string},
        "deviceId": {string},
        "networkIds": {array},
        "deviceTypeIds": {array},
        "names": {array},
        "timestamp": {datetime}
    }]
}
```

**Payload Parameters**

| Property Name                | Type     | Description                                                                                             |
| :--------------------------- | :------- | :------------------------------------------------------------------------------------------------------ |
| action                       | string   | Action name: subscription/list                                                                          |
| status                       | string   | Operation execution status (success or error).                                                          |
| requestId                    | object   | Request unique identifier as specified in the request message.                                          |
| subscriptions                | array    | JSON with information about user subscriptions.                                                         |
| subscriptions.subscriptionId | integer  | Subscription unique identifier.                                                                         |
| subscriptions.type           | string   | Type of subscription, possible values: 'command' or 'notification'.                                     |
| subscriptions.deviceId       | string   | Subscription unique device identifier. 'Null' means subscription to all available devices.              |
| subscriptions.networkIds     | array    | List of subscribed unique network identifiers. 'Null' means subscription to all available networks.     |
| subscriptions.deviceTypeIds  | array    | List of subscribed unique device type identifiers. 'Null' means subscription to all available networks. |
| subscriptions.names          | array    | List of subscribed names. 'Null' means subscription to all available notification/command names.        |
| subscriptions.timestamp      | datetime | Subscription starting timestamp (UTC).                                                                  |
