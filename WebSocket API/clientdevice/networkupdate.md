---
title: "network/update"
slug: "networkupdate"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jul 28 2017 16:19:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Updates a network.

## Request Message

**Authorization**

Access JSON Web Token (ManageNetwork)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "networkId": {string},
    "network": {
        "name": {string},
        "description": {string}
    }
}
```

**Message Parameters**

|                     |     |        |                                                                         |
| :------------------ | :-- | :----- | :---------------------------------------------------------------------- |
| action              | Yes | string | Action name: network/update                                             |
| requestId           | No  | object | Request unique identifier, will be passed back in the response message. |
| networkId           | Yes | string | Network unique identifier.                                              |
| network             | Yes | object | [Network](doc:network) resource to insert.                              |
| network.name        | No  | string | Network display name.                                                   |
| network.description | No  | string | Network short description.                                              |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object}
}
```

**Message Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: network/update                                    |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
