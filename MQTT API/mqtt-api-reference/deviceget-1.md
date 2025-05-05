---
title: "device/get"
slug: "deviceget-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:54:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:26:42 GMT+0000 (Coordinated Universal Time)"
---
Gets information about the current device.

**Authorization**

Access JSON Web Token (GetDevice)

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
    "deviceId": {string}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                                                                          |
| :------------ | :------- | :----- | :------------------------------------------------------------------------------------------------------------------- |
| action        | Yes      | string | Action name: device/get                                                                                              |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message.                                              |
| deviceId      | Yes      | string | Device unique identifier, if not specified the device for the principal will be passed back in the response message. |

## Response Topic and Payload

**Topic**

```text
dh/response/device/get@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "device": {
        "id": {string},
        "name": {string},
        "status": {string},
        "data": {object},
        "networkId": {integer},
        "isBlocked": {boolean}
    }
}
```

**Payload Parameters**

| Property Name    | Type    | Description                                                        |
| :--------------- | :------ | :----------------------------------------------------------------- |
| action           | string  | Action name: device/get                                            |
| status           | string  | Operation execution status (success or error).                     |
| requestId        | object  | Request unique identifier as specified in the request message.     |
| device           | object  | The [Device](doc:device) resource representing the current device. |
| device.id        | string  | Device unique identifier.                                          |
| device.name      | string  | Device display name.                                               |
| device.data      | object  | Device data, a JSON object with an arbitrary structure.            |
| device.networkId | integer | Network identifier.                                                |
| device.isBlocked | boolean | Device isBlocked identifier.                                       |
