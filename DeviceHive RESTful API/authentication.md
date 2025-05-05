---
title: "Authentication"
slug: "authentication"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 12:28:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 15 2018 15:04:25 GMT+0000 (Coordinated Universal Time)"
---
Provides a mechanism of authentication to this API using JSON Web Tokens.

## Methods

| Method                                         | Authorization                        | Uri                            | Description                                                                         |
| :--------------------------------------------- | :----------------------------------- | :----------------------------- | :---------------------------------------------------------------------------------- |
| [login](doc:login)                             | None                                 | POST /token                    | Creates and returns access and refresh tokens for the given user.                   |
| [create](doc:create)                           | Access JSON Web Token (ManageToken)  | POST /token/create             | Creates and returns access and refresh tokens for the given user and access rights. |
| [refresh](doc:refresh)                         | None                                 | POST /token/refresh            | Creates and returns a new access token for the given refresh token.                 |
| [plugin/create](doc:plugin/create)             | Access JSON Web Token (ManagePlugin) | POST /token/plugin/create      | Creates JWT access and refresh tokens for plugin                                    |
| [plugin/authenticate](doc:plugin/authenticate) | None                                 | GET /token/plugin/authenticate | Authenticates a plugin and JWT Plugin payload.                                      |

## Resource Representation

```text
{
    "userId": {integer},
    "expiration": {datetime},
    "actions": {array},
    "networkIds": {array},
    "deviceIds": {array}
}
```

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "userId",
    "0-1": "integer",
    "0-2": "User identifier.",
    "1-0": "expiration",
    "1-1": "datetime",
    "1-2": "Expiration date (UTC).",
    "2-0": "actions",
    "2-1": "array",
    "2-2": "A collection of allowed actions. Available values:  \nGetNetwork: get information about network  \nGetDevice: get information about device and device class  \nGetDeviceState: get information about current device equipment state  \nGetDeviceNotification: get or subscribe to device notifications  \nGetDeviceCommand: get or subscribe to commands sent to device  \nRegisterDevice: register a device  \nCreateDeviceNotification: post notifications on behalf of device  \nCreateDeviceCommand: post commands to device  \nUpdateDeviceCommand: update status of commands on behalf of device",
    "3-0": "networkIds",
    "3-1": "array",
    "3-2": "A collection of identifiers of allowed networks. Only API requests for devices within the allowed networks will be authorized with this permission. Set to null to allow callees to access all networks permitted for the owner user.",
    "4-0": "deviceIds",
    "4-1": "array",
    "4-2": "A collection of unique identifiers of allowed devices. Only API requests for allowed devices will be authorized with this permission. Set to null to allow callees to access all devices permitted for the owner user."
  },
  "cols": 3,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Available actions:

JWT tokens contain user-related information and permissions list which could be represented with ids or action names.

| Action                       | String                   | Id |
| :--------------------------- | :----------------------- | :- |
| Any                          | \*                       | 0  |
| None                         | null                     | 1  |
| Get Network                  | GetNetwork               | 2  |
| Get Device                   | GetDevice                | 3  |
| Get Device Notification      | GetDeviceNotification    | 4  |
| Get Device Command           | GetDeviceCommand         | 5  |
| Register Device              | RegisterDevice           | 6  |
| Create Device Command        | CreateDeviceCommand      | 7  |
| Update Device Command        | UpdateDeviceCommand      | 8  |
| Create Device Notification   | CreateDeviceNotification | 9  |
| Get Current User             | GetCurrentUser           | 10 |
| Update Current User          | UpdateCurrentUser        | 11 |
| Manage User (admin)          | ManageUser               | 12 |
| Manage Configuration (admin) | ManageConfiguration      | 13 |
| Manage Network (admin)       | ManageNetwork            | 14 |
| Manage Token                 | ManageToken              | 15 |
| Manage Plugin                | ManagePlugin             | 16 |
| Get Device Type              | GetDeviceType            | 17 |
| Manage Device Type (admin)   | ManageDeviceType         | 18 |
