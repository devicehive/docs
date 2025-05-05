---
title: "token/create"
slug: "tokencreate"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Sat Jul 15 2017 13:00:03 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 15 2018 15:10:02 GMT+0000 (Coordinated Universal Time)"
---
Creates access and refresh tokens by payload.

## Request Message

**Authorization**

Access JSON Web Token (ManageToken)

Available actions are listed [here](doc:authentication#section-available-actions).

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "payload": {
        "userId": {object},
        "actions": {array},
        "networkIds": {array},
        "deviceTypeIds": {array},
        "expiration": {datetime}
    }
}
```

**Message Parameters**

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Required",
    "h-2": "Type",
    "h-3": "Description",
    "0-0": "action",
    "0-1": "Yes",
    "0-2": "string",
    "0-3": "Action name: token/create",
    "1-0": "requestId",
    "1-1": "No",
    "1-2": "object",
    "1-3": "Request unique identifier, will be passed back in the response message.",
    "2-0": "payload",
    "2-1": "Yes",
    "2-2": "object",
    "2-3": "User payload with specific permissions",
    "3-0": "payload.userId",
    "3-1": "Yes",
    "3-2": "integer",
    "3-3": "User identifier.",
    "4-0": "payload.actions",
    "4-1": "No",
    "4-2": "array",
    "4-3": "A collection of allowed actions. Available values:  \n  _ GetNetwork: get information about network  \n  _ GetDevice: get information about device and device class  \n  _ GetDeviceNotification: get or subscribe to device notifications  \n  _ GetDeviceCommand: get or subscribe to commands sent to device  \n  _ RegisterDevice: register a device  \n  _ CreateDeviceNotification: post notifications on behalf of device  \n  _ CreateDeviceCommand: post commands to device  \n  _ UpdateDeviceCommand: update status of commands on behalf of device  \n  _ GetCurrentUser: get current user info  \n  _ UpdateCurrentUser: update current user  \n  _ ManageUser: admin permission for managing all users  \n  _ ManageConfiguration: admin permission for managing server configuration  \n  _ ManageNetwork: admin permission for managing all networks and its devices  \n  _ ManageToken: admin permission for creating tokens ",
    "5-0": "payload.networkIds",
    "5-1": "No",
    "5-2": "array",
    "5-3": "A collection of identifiers of allowed networks. Only API requests for devices within the allowed networks will be authorized with this permission. Set to null to allow callees to access all networks permitted for the owner user.",
    "6-0": "payload.deviceTypeIds",
    "6-1": "No",
    "6-2": "array",
    "6-3": "A collection of unique identifiers of allowed device types. Only API requests for allowed device types will be authorized with this permission. Set to null to allow callees to access all devices permitted for the owner user.",
    "7-0": "payload.expiration",
    "7-1": "No",
    "7-2": "datetime",
    "7-3": "Expiration date (UTC)."
  },
  "cols": 4,
  "rows": 8,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Response Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "accessToken": {string},
    "refreshToken": {string}
}
```

**Message Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: token                                             |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
| accessToken   | string | JSON Web Token for authorization.                              |
| refreshToken  | string | JSON Web Token for refreshing access token.                    |
