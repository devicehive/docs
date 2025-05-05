---
title: "devicetype/get"
slug: "devicetypeget"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Jan 11 2018 10:32:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jan 11 2018 11:15:10 GMT+0000 (Coordinated Universal Time)"
---
Gets information about device type and its devices.

## Request Message

**Authorization**

Access JSON Web Token (GetDeviceType)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceTypeId": {int}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: devicetype/get                                             |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| deviceTypeId  | Yes      | int    | Device type unique identifier.                                          |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "deviceType": {
        "id": {int},
        "name": {string},
        "description": {string},
        "devices": [{object}]
    }
}
```

**Message Parameters**

| Property Name          | Type   | Description                                                          |
| :--------------------- | :----- | :------------------------------------------------------------------- |
| action                 | string | Action name: devicetype/get                                          |
| status                 | string | Operation execution status (success or error).                       |
| requestId              | object | Request unique identifier as specified in the request message.       |
| deviceType             | object | [DeviceType](doc:devicetype) resource with the list of it's devices. |
| deviceType.id          | int    | Device type identifier.                                              |
| deviceType.name        | string | Device type name.                                                    |
| deviceType.description | string | Device type description.                                             |
| deviceType.devices     | object | List of [Devices] \(doc:device), associated with the device type.    |
