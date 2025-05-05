---
title: "network/count"
slug: "networkcount-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:56:34 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:28:58 GMT+0000 (Coordinated Universal Time)"
---
Gets count of networks.

**Authorization**

Access JSON Web Token (GetNetwork)

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
    "namePattern": {string}
}
```

**Payload Parameters**

| Property name | Required | Type   | Description                                                                    |
| :------------ | :------- | :----- | :----------------------------------------------------------------------------- |
| action        | Yes      | string | Action name: network/count                                                     |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message.        |
| name          | No       | string | Filter by network name.                                                        |
| namePattern   | No       | string | Filter by network name pattern. In pattern wildcards '%' and '\_' can be used. |

## Response Topic and Payload

**Topic**

```text
dh/response/network/count@{clientId}
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
| action        | string  | Action name: network/count                                     |
| requestId     | object  | Request unique identifier as specified in the request message. |
| status        | string  | Operation execution status (success or error).                 |
| count         | integer | Number of networks that match the filters.                     |
