---
title: "put"
slug: "put"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 07:27:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu May 03 2018 13:46:47 GMT+0000 (Coordinated Universal Time)"
---
Creates new or updates existing property.

## Request

**HTTP Request**

```text
PUT /configuration/{name}
```

**Parameters**

| Parameter Name | Required | Type   | Description                  |
| :------------- | :------- | :----- | :--------------------------- |
| name           | Yes      | string | Configuration parameter name |

**Authorization**  
JSON Web Token (ManageConfiguration)

**Request Body**  
In the request body supply value of [Configuration](doc:configuration) resource

| Property Name | Required | Type   | Description                   |
| :------------ | :------- | :----- | :---------------------------- |
| value         | Yes      | string | Configuration parameter value |

## Response

If successful, this method returns a [Configuration](doc:configuration) resource in the response body.

| Property Name | Type    | Description                                                 |
| :------------ | :------ | :---------------------------------------------------------- |
| name          | string  | Configuration parameter name.                               |
| value         | string  | Configuration parameter value.                              |
| entityVersion | integer | Specifies the version field or property of an entity class. |
