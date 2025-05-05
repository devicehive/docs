---
title: "get"
slug: "get-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 07:27:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Returns requested property value.

## Request

**HTTP Request**

```text
GET /configuration/{name}
```

**Parameters**

| Parameter Name | Required | Type   | Description                   |
| :------------- | :------- | :----- | :---------------------------- |
| name           | yes      | string | Configuration parameter name. |

**Authorization**

JSON Web Token (ManageConfiguration)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns a [Configuration](doc:configuration) resource in the response body.

| Property Name | Type    | Description                                                 |
| :------------ | :------ | :---------------------------------------------------------- |
| name          | string  | Configuration parameter name.                               |
| value         | string  | Configuration parameter value.                              |
| entityVersion | integer | Specifies the version field or property of an entity class. |
