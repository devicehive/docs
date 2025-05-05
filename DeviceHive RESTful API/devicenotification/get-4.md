---
title: "get"
slug: "get-4"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 14:28:49 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 15:33:05 GMT+0000 (Coordinated Universal Time)"
---
Gets information about device notification.

## Request

**HTTP Request**

```text
GET /device/{deviceId}/notification/{id}
```

**Parameters**

| Parameter Name | Required | Type    | Description               |
| :------------- | :------- | :------ | :------------------------ |
| deviceId       | Yes      | string  | Device unique identifier. |
| id             | Yes      | integer | Notification identifier.  |

**Authorization**

Access JSON Web Token (GetDeviceNotification)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns a [DeviceNotification](doc:devicenotification)  resource in the response body.

| Property Name | Type     | Description                                                                                               |
| :------------ | :------- | :-------------------------------------------------------------------------------------------------------- |
| id            | integer  | Notification identifier.                                                                                  |
| notification  | string   | Notification name.                                                                                        |
| deviceId      | string   | Device unique identifier.                                                                                 |
| networkId     | integer  | Network unique identifier.                                                                                |
| timestamp     | datetime | Notification UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| parameters    | object   | Notification parameters, a JSON object with an arbitrary structure.                                       |
