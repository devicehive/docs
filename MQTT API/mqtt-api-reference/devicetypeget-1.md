---
title: "devicetype/get"
slug: "devicetypeget-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:55:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:28:05 GMT+0000 (Coordinated Universal Time)"
---
Gets information about device type and its devices.

**Authorization**

Access JSON Web Token (GetDeviceType)

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
    "deviceTypeId": {int}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: devicetype/get                                             |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| deviceTypeId  | Yes      | int    | Device type unique identifier.                                          |

## Response Topic and Payload

**Topic**

```text
dh/response/devicetype/get@{clientId}
```

**Payload Representation**

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

**Payload Parameters**

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
