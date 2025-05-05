---
title: "insert"
slug: "insert-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 14:28:56 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 16:51:34 GMT+0000 (Coordinated Universal Time)"
---
Creates new device notification.

## Request

**HTTP Request**

```text
POST /device/{deviceId}/notification
```

**Parameters**

| Parameter Name | Required | Type   | Description               |
| :------------- | :------- | :----- | :------------------------ |
| deviceId       | Yes      | string | Device unique identifier. |

**Authorization**

Access JSON Web Token (CreateDeviceNotification)

**Request Body**

In the request body, supply a [DeviceNotification](doc:devicenotification)  resource.

| Property Name | Required | Type     | Description                                                         |
| :------------ | :------- | :------- | :------------------------------------------------------------------ |
| notification  | Yes      | string   | Notification name                                                   |
| timestamp     | No       | datetime | Notification timestamp (UTC)                                        |
| parameters    | No       | object   | Notification parameters, a JSON object with an arbitrary structure. |

## Response

If successful, this method returns a [DeviceNotification](doc:devicenotification)  resource in the response body.

| Property Name | Type     | Description                                                                                               |
| :------------ | :------- | :-------------------------------------------------------------------------------------------------------- |
| id            | integer  | Notification identifier.                                                                                  |
| timestamp     | datetime | Notification UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
