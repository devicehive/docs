---
title: "cluster/info"
slug: "clusterinfo"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 19 2017 11:35:47 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Returns information about cluster (Kafka, Zookeeper etc.)

## Request Message

**Authorization**

None

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: cluster/info                                               |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |

## Response Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "clusterInfo": {
        "bootstrap.servers": {string},
        "zookeper.connect": {string}
    }
}
```

**Message Parameters**

| Property Name     | Type     | Description                                                    |
| :---------------- | :------- | :------------------------------------------------------------- |
| action            | string   | Action name: cluster/info                                      |
| status            | string   | Operation execution status (success or error).                 |
| requestId         | object   | Request unique identifier as specified in the request message. |
| clusterinfo       | object   | The information about cluster.                                 |
| bootstrap.serves  | string   | Bootstrap servers address.                                     |
| zookeeper.connect | datetime | Zookeeper servers address.                                     |
