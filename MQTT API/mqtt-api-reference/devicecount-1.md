---
title: "device/count"
slug: "devicecount-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:54:53 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:27:04 GMT+0000 (Coordinated Universal Time)"
---
Gets count of devices.

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
    "networkName": {string}
}
```

**Payload Parameters**

| Property name | Required | Type   | Description                                                                   |
| :------------ | :------- | :----- | :---------------------------------------------------------------------------- |
| action        | Yes      | string | Action name: device/count                                                     |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message.       |
| name          | No       | string | Filter by device name.                                                        |
| namePattern   | No       | string | Filter by device name pattern. In pattern wildcards '%' and '\_' can be used. |
| networkId     | No       | long   | Filter by associated network identifier.                                      |
| networkName   | No       | string | Filter by associated network name.                                            |

## Response Topic and Payload

**Topic**

```text
dh/response/device/count@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "status": {string},
    "count": {integer}
}
```

**Payload Parameters**

| Property Name | Type    | Description                                                    |
| :------------ | :------ | :------------------------------------------------------------- |
| action        | string  | Action name: device/count                                      |
| requestId     | object  | Request unique identifier as specified in the request message. |
| status        | string  | Operation execution status (success or error).                 |
| count         | integer | Number of devices that match the filters.                      |
