---
title: "network/list"
slug: "networklist"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jul 28 2017 15:56:59 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets the list of networks.

## Request Message

**Authorization**

Access JSON Web Token (GetNetwork)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "name": {string},
    "namePattern": {string},
    "sortField": {string},
    "sortOrder": {string},
    "take": {integer},
    "skip": {integer}
}
```

**Message Parameters**

| Property name | Required | Type    | Description                                                                        |
| :------------ | :------- | :------ | :--------------------------------------------------------------------------------- |
| action        | Yes      | string  | Action name: network/list                                                          |
| requestId     | No       | object  | Request unique identifier, will be passed back in the response message.            |
| name          | No       | string  | Filter by network name.                                                            |
| namePattern   | No       | string  | Filter by network name pattern. In pattern wildcards '%' and '\_' can be used.     |
| sortField     | No       | string  | Result list sort field.                                                            |
| sortOrder     | No       | string  | Result list sort order. Values are ASC and DES. The sortField should be specified. |
| take          | No       | integer | Number of records to take from the result list.                                    |
| skip          | No       | integer | Number of records to skip from the result list.                                    |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "status": {string},
    "networks": [{
        "id": {string},
        "name": {string},
        "description": {string}
    }]
}
```

**Message Parameters**

| Property Name       | Type   | Description                                                          |
| :------------------ | :----- | :------------------------------------------------------------------- |
| action              | string | Action name: network/list                                            |
| requestId           | object | Request unique identifier as specified in the request message.       |
| status              | string | Operation execution status (success or error).                       |
| networks            | array  | The array of networks.                                               |
| network             | object | The [Network](doc:network)   resource representing the user network. |
| network.id          | string | Network unique identifier.                                           |
| network.name        | string | Network display name.                                                |
| network.description | string | Network short description.                                           |
