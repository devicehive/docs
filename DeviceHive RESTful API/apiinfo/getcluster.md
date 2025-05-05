---
title: "getCluster"
slug: "getcluster"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 07:14:53 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Returns information about cluster (Kafka, Zookeeper etc.)

## Request

**HTTP Request**

```text
GET /info/config/cluster
```

**Authorization**

None

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns a cluster information in the response body.

| Property Name     | Type   | Description                |
| :---------------- | :----- | :------------------------- |
| bootstrap.servers | string | Bootstrap servers address. |
| zookeeper.connect | string | Zookeeper servers address. |
