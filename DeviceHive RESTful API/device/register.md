---
title: "register"
slug: "register"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jul 04 2017 09:59:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Registers or updates a device. For initial device registration, only 'name' and 'deviceClass' properties are required.

## Request

**HTTP Request**

```text
PUT /device/{id}
```

**Parameters**

[block:parameters]
{
  "data": {
    "h-0": "Parameter Name",
    "h-1": "Required",
    "h-2": "Type",
    "h-3": "Description",
    "0-0": "id",
    "0-1": "Yes",
    "0-2": "string",
    "0-3": "Device unique identifier.  \nDevice Id can only contain letters, digits and dashes."
  },
  "cols": 4,
  "rows": 1,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


**Authorization**

Access JSON Web Token (RegisterDevice)

**Request Body**

In the request body, supply a [Device](doc:device) resource.

| Property Name | Required | Type    | Description                                             |
| :------------ | :------- | :------ | :------------------------------------------------------ |
| name          | Yes      | string  | Device display name.                                    |
| data          | No       | object  | Device data, a JSON object with an arbitrary structure. |
| networkId     | Yes      | integer | Associated network id.                                  |
| isBlocked     | No       | boolean | Indicates whether device is blocked.                    |

## Response

If successful, this method returns an empty response body.
