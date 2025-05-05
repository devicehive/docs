---
title: "devicetype/insert"
slug: "devicetypeinsert-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:55:55 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:28:18 GMT+0000 (Coordinated Universal Time)"
---
Creates new device type.

**Authorization**

Access JSON Web Token (ManageDeviceType)

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
    "deviceType": {
        "name": {string},
        "description": {string}
    }
}
```

**Payload Parameters**

|                        |     |        |                                                                         |
| :--------------------- | :-- | :----- | :---------------------------------------------------------------------- |
| action                 | Yes | string | Action name: devicetype/insert                                          |
| requestId              | No  | object | Request unique identifier, will be passed back in the response message. |
| deviceType             | Yes | object | [DeviceType](doc:devicetype) resource to insert.                        |
| deviceType.name        | No  | string | Device type name.                                                       |
| deviceType.description | No  | string | Device type description.                                                |

## Response Topic and Payload

**Topic**

```text
dh/response/devicetype/insert@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "deviceType": {
        "id": {int}
    }
}
```

**Payload Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: devicetype/insert                                 |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
| deviceType.id | int    | Device type identifier.                                        |
