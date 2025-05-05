---
title: "create"
slug: "create"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 13:01:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 15 2018 15:07:48 GMT+0000 (Coordinated Universal Time)"
---
Creates and returns access and refresh tokens for the given user and access rights.

## Request

**HTTP Request**

```text
POST /token/create
```

**Authorization**

Access JSON Web Token (ManageToken)

**Request Body**

In the request body, supply user identifier, rights and expiration date.

Available actions are listed [here](doc:authentication#section-available-actions).

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Required",
    "h-2": "Type",
    "h-3": "Description",
    "0-0": "userId",
    "0-1": "Yes",
    "0-2": "integer",
    "0-3": "User identifier.",
    "1-0": "expiration",
    "1-1": "No",
    "1-2": "datetime",
    "1-3": "Expiration date (UTC).",
    "2-0": "actions",
    "2-1": "No",
    "2-2": "array",
    "2-3": "A collection of allowed actions. Available values:  \nGetNetwork: get information about network  \nGetDevice: get information about device and device class  \nGetDeviceState: get information about current device equipment state  \nGetDeviceNotification: get or subscribe to device notifications  \nGetDeviceCommand: get or subscribe to commands sent to device  \nRegisterDevice: register a device  \nCreateDeviceNotification: post notifications on behalf of device  \nCreateDeviceCommand: post commands to device  \nUpdateDeviceCommand: update status of commands on behalf of device",
    "3-0": "networkIds",
    "3-1": "No",
    "3-2": "array",
    "3-3": "A collection of identifiers of allowed networks. Only API requests for devices within the allowed networks will be authorized with this permission. Set to null to allow callees to access all networks permitted for the owner user.",
    "4-0": "deviceTypeIds",
    "4-1": "No",
    "4-2": "array",
    "4-3": "A collection of unique identifiers of allowed device types. Only API requests for allowed device types will be authorized with this permission. Set to null to allow callees to access all devices permitted for the owner user."
  },
  "cols": 4,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Response

If successful, this method returns a pair of access and refresh tokens.

| Property Name | Type   | Description             |
| :------------ | :----- | :---------------------- |
| accessToken   | string | Access JSON Web Token.  |
| refreshToken  | string | Refresh JSON Web Token. |
