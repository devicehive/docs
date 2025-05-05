---
title: "device/list"
slug: "devicelist-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:54:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:26:53 GMT+0000 (Coordinated Universal Time)"
---
Gets the list of devices.

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
    "name": {string},
    "namePattern": {string},
    "networkId": {long},
    "networkName": {string},
    "sortField": {string},
    "sortOrder": {string},
    "take": {integer},
    "skip": {integer}
}
```

**Payload Parameters**

| Property name | Required | Type    | Description                                                                                   |
| :------------ | :------- | :------ | :-------------------------------------------------------------------------------------------- |
| action        | Yes      | string  | Action name: device/list                                                                      |
| requestId     | No       | object  | Request unique identifier, will be passed back in the response message.                       |
| name          | No       | string  | Filter by device name.                                                                        |
| namePattern   | No       | string  | Filter by device name pattern. In pattern wildcards '%' and '\_' can be used.                 |
| networkId     | No       | long    | Filter by associated network identifier.                                                      |
| networkName   | No       | string  | Filter by associated network name.                                                            |
| sortField     | No       | string  | Result list sort field. Available values are name and network.                                |
| sortOrder     | No       | string  | Result list sort order. Available values are ASC and DESC. The sortField should be specified. |
| take          | No       | integer | Number of records to take from the result list.                                               |
| skip          | No       | integer | Number of records to skip from the result list.                                               |

## Response Topic and Payload

**Topic**

```text
dh/response/device/list@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "status": {string},
    "devices": [{
        "id": {string},
        "name": {string},
        "status": {string},
        "data": {object},
        "networkId": {integer},
        "isBlocked": {boolean},
    }]
}
```

**Payload Parameters**

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "action",
    "0-1": "string",
    "0-2": "Action name: device/list",
    "1-0": "requestId",
    "1-1": "object",
    "1-2": "Request unique identifier as specified in the request message.",
    "2-0": "status",
    "2-1": "string",
    "2-2": "Operation execution status (success or error).",
    "3-0": "devices",
    "3-1": "array",
    "3-2": "The array of devices.",
    "4-0": "device",
    "4-1": "object",
    "4-2": "The [Device](doc:device)  resource representing the user device.",
    "5-0": "device.id",
    "5-1": "string",
    "5-2": "Device unique identifier.",
    "6-0": "device.name",
    "6-1": "string",
    "6-2": "Device display name.",
    "7-0": "device.status",
    "7-1": "string",
    "7-2": "Device operation status. The status is optional and it can be set to an arbitrary value, if applicable.  \nIf device status monitoring feature is enabled, the framework will set status value to 'Offline' after defined period of inactivity.",
    "8-0": "device.data",
    "8-1": "object",
    "8-2": "Device data, a JSON object with an arbitrary structure.",
    "9-0": "device.networkId",
    "9-1": "integer",
    "9-2": "Network identifier.",
    "10-0": "device.isBlocked",
    "10-1": "boolean",
    "10-2": "Device isBlocked identifier."
  },
  "cols": 3,
  "rows": 11,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]
