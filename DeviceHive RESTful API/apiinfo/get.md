---
title: "get"
slug: "get"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 07:14:34 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets meta-information of the current API.

## Request

**HTTP Request**

```text
GET /info
```

**Authorization**

None

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns a [ApiInfo](doc:apiinfo) resource in the response body.

| Property Name      | Type     | Description               |
| :----------------- | :------- | :------------------------ |
| apiVersion         | string   | API version.              |
| serverTimestamp    | datetime | Current server timestamp. |
| webSocketServerUrl | string   | WebSocket server URL.     |
