---
title: "cluster/info"
slug: "clusterinfo-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:01:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:33:06 GMT+0000 (Coordinated Universal Time)"
---
Returns information about cluster (Kafka, Zookeeper etc.)

**Authorization**

None

## Request Topic and Payload

**Topic**

```text
dh/request
```

**Payload Representation**

```text
{
    "action": {string},
    "requestId": {object}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: cluster/info                                               |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |

## Response Topic and Payload

**Topic**

```text
dh/response/authenticate@{clientId}
```

**Payload Representation**

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

**Payload Parameters**

| Property Name     | Type     | Description                                                    |
| :---------------- | :------- | :------------------------------------------------------------- |
| action            | string   | Action name: cluster/info                                      |
| status            | string   | Operation execution status (success or error).                 |
| requestId         | object   | Request unique identifier as specified in the request message. |
| clusterinfo       | object   | The information about cluster.                                 |
| bootstrap.serves  | string   | Bootstrap servers address.                                     |
| zookeeper.connect | datetime | Zookeeper servers address.                                     |
