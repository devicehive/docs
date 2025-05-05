---
title: "device/get"
slug: "deviceget"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jul 14 2017 14:55:03 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 18 2018 16:16:25 GMT+0000 (Coordinated Universal Time)"
---
Gets information about the current device.

## Request Message

**Authorization**

Access JSON Web Token (GetDevice)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                                                                          |
| :------------ | :------- | :----- | :------------------------------------------------------------------------------------------------------------------- |
| action        | Yes      | string | Action name: device/get                                                                                              |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message.                                              |
| deviceId      | Yes      | string | Device unique identifier, if not specified the device for the principal will be passed back in the response message. |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "device": {
        "id": {string},
        "name": {string},
        "data": {object},
        "networkId": {integer},
        "isBlocked": {boolean}
    }
}
```

**Message Parameters**

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
