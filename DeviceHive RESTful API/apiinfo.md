---
title: "ApiInfo"
slug: "apiinfo"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 12:28:58 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Represents meta-information about the current API.

## Methods

| Method                       | Authorization | Uri                      | Description                                               |
| :--------------------------- | :------------ | :----------------------- | :-------------------------------------------------------- |
| [get](doc:get)               | None          | GET /info                | Gets meta-information of the current API.                 |
| [getCluster](doc:getcluster) | None          | GET /info/config/cluster | Returns information about cluster (Kafka, Zookeeper etc.) |

## Resource Representation

```text
{
    "apiVersion": {string},
    "serverTimestamp": {datetime},
    "webSocketServerUrl": {string}
}
```

| Property Name      | Type     | Description               |
| :----------------- | :------- | :------------------------ |
| apiVersion         | string   | API version               |
| serverTimestamp    | datetime | Current server timestamp. |
| webSocketServerUrl | string   | WebSocket server URL.     |
