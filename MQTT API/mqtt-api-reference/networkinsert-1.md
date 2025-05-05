---
title: "network/insert"
slug: "networkinsert-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:56:55 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:29:20 GMT+0000 (Coordinated Universal Time)"
---
Inserts new network.

**Authorization**

Access JSON Web Token (ManageNetwork)

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
    "network": {
        "name": {string},
        "description": {string}
    }
}
```

**Payload Parameters**

|                     |     |        |                                                                         |
| :------------------ | :-- | :----- | :---------------------------------------------------------------------- |
| action              | Yes | string | Action name: network/insert                                             |
| requestId           | No  | object | Request unique identifier, will be passed back in the response message. |
| network             | Yes | object | [Network](doc:network) resource to insert.                              |
| network.name        | No  | string | Network display name.                                                   |
| network.description | No  | string | Network short description.                                              |

## Response Topic and Payload

**Topic**

```text
dh/response/network/insert@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "network": {
        "id": {int}
    }
}
```

**Payload Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: network/insert                                    |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
| network.id    | int    | Created network ID.                                            |
