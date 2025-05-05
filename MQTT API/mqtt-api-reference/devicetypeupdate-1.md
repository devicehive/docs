---
title: "devicetype/update"
slug: "devicetypeupdate-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:56:03 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:28:27 GMT+0000 (Coordinated Universal Time)"
---
Updates an existing device type.

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
    "deviceTypeId": {string},
    "deviceType": {
        "name": {string},
        "description": {string}
    }
}
```

**Payload Parameters**

|                        |     |        |                                                                         |
| :--------------------- | :-- | :----- | :---------------------------------------------------------------------- |
| action                 | Yes | string | Action name: devicetype/update                                          |
| requestId              | No  | object | Request unique identifier, will be passed back in the response message. |
| deviceTypeId           | Yes | string | Device type identifier.                                                 |
| deviceType             | Yes | object | [DeviceType](doc:devicetype) resource for update.                       |
| deviceType.name        | No  | string | Device type name.                                                       |
| deviceType.description | No  | string | Device type description.                                                |

## Response Topic and Payload

**Topic**

```text
dh/response/devicetype/update@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object}
}
```

**Payload Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: devicetype/update                                 |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
