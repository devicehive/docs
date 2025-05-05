---
title: "network/get"
slug: "networkget-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:56:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:29:09 GMT+0000 (Coordinated Universal Time)"
---
Gets a network by ID.

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
    "networkId": {int}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: network/get                                                |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| networkId     | Yes      | int    | Network unique identifier.                                              |

## Response Topic and Payload

**Topic**

```text
dh/response/network/get@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "network": {
        "id": {int},
        "name": {string},
        "description": {string},
        "devices": [{object}]
    }
}
```

**Payload Parameters**

| Property Name       | Type   | Description                                                           |
| :------------------ | :----- | :-------------------------------------------------------------------- |
| action              | string | Action name: network/get                                              |
| status              | string | Operation execution status (success or error).                        |
| requestId           | object | Request unique identifier as specified in the request message.        |
| network             | object | The [Network](doc:network) resource representing the current network. |
| network.id          | int    | Network unique identifier.                                            |
| network.name        | string | Network display name.                                                 |
| network.description | string | Network short description.                                            |
| network.devices     | object | Network's devices list.                                               |
