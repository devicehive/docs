---
title: "count"
slug: "count-2"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jan 09 2018 13:26:49 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jan 09 2018 14:28:04 GMT+0000 (Coordinated Universal Time)"
---
Gets count of users.

## Request

**HTTP Request**

```text
GET /user/count
```

**Parameters**

| Parameter Name | Required | Type    | Description                                                         |
| :------------- | :------- | :------ | :------------------------------------------------------------------ |
| login          | No       | string  | Filter by user login                                                |
| loginPattern   | No       | string  | Filter by user login pattern                                        |
| role           | No       | integer | Filter by user role. 0 is Administrator, 1 is Client.               |
| status         | No       | integer | Filter by user status. 0 is Active, 1 is Locked Out, 2 is Disabled. |

**Authorization**

Access JSON Web Token (ManageUser)

**Request Body**

Do not supply a request body with this method.

## Response

If successful, this method returns the count of [User](doc:user)  resources in the response body.

| Property Name | Type    | Description                             |
| :------------ | :------ | :-------------------------------------- |
| count         | integer | Number of users that match the filters. |
