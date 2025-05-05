---
title: "network/get"
slug: "networkget"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jul 28 2017 15:16:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets a network by ID.

## Request Message

**Authorization**

Access JSON Web Token (GetNetwork)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "networkId": {int}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: network/get                                                |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| networkId     | Yes      | int    | Network unique identifier.                                              |

## Server Message

**Message Representation**

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

**Message Parameters**

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
