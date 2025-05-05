---
title: "User"
slug: "user"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 12:30:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 23 2018 12:33:35 GMT+0000 (Coordinated Universal Time)"
---
Represents a user to this API.

## Methods

[block:parameters]
{
  "data": {
    "h-0": "Method",
    "h-1": "Authorization",
    "h-2": "Uri",
    "h-3": "Description",
    "0-0": "[list](doc:list-2)",
    "0-1": "Access JSON Web Token (ManageUser)",
    "0-2": "GET /user",
    "0-3": "Gets list of users.",
    "1-0": "[count](doc:count-2)",
    "1-1": "Access JSON Web Token (ManageUser)",
    "1-2": "GET /user/count",
    "1-3": "Gets count of users.",
    "2-0": "[get](doc:get-6)",
    "2-1": "Access JSON Web Token (GetCurrentUser)",
    "2-2": "GET /user/{id}",
    "2-3": "Gets information about user and its assigned networks.  \nOnly administrators are allowed to get information about any user. User-level accounts can only retrieve information about themselves.",
    "3-0": "[insert](doc:insert-3)",
    "3-1": "Access JSON Web Token (ManageUser)",
    "3-2": "POST /user",
    "3-3": "Creates new user.",
    "4-0": "[update](doc:update-2)",
    "4-1": "Access JSON Web Token (UpdateCurrentUser)",
    "4-2": "PUT /user/{id}",
    "4-3": "Updates an existing user.  \nOnly administrators are allowed to update any property of any user. User-level accounts can only change their own password in case:  \n  _ They already have a password.  \n  _ They provide a valid current password in the 'oldPassword' property. ",
    "5-0": "[delete](doc:delete-3)",
    "5-1": "Access JSON Web Token (ManageUser)",
    "5-2": "DELETE /user/{id}",
    "5-3": "Deletes an existing user.",
    "6-0": "[getCurrent](doc:getcurrent)",
    "6-1": "Access JSON Web Token (ManageUser)",
    "6-2": "GET /user/current",
    "6-3": "Gets information about user/network association.  \nOnly administrators are allowed to get information about any user. User-level accounts can only retrieve information about themselves.",
    "7-0": "[updateCurrent](doc:updatecurrent)",
    "7-1": "Access JSON Web Token (ManageUser)",
    "7-2": "PUT /user/current",
    "7-3": "Updates the current user.  \nOnly administrators are allowed to update any property of any user. User-level accounts can only change their own password in case:  \n  _ They already have a password.  \n  _ They provide a valid current password in the 'oldPassword' property. ",
    "8-0": "[getNetwork](doc:getnetwork)",
    "8-1": "Access JSON Web Token (ManageUser)",
    "8-2": "GET /user/{id}/network/{networkId}",
    "8-3": "Gets information about user/network association.",
    "9-0": "[assignNetwork](doc:assignnetwork)",
    "9-1": "Access JSON Web Token (ManageUser)",
    "9-2": "PUT /user/{id}/network/{networkId}",
    "9-3": "Associates network with the user.",
    "10-0": "[unassignNetwork](doc:unassignnetwork)",
    "10-1": "Access JSON Web Token (ManageUser)",
    "10-2": "DELETE /user/{id}/network/{networkId}",
    "10-3": "Removes association between network and user.",
    "11-0": "[assignDeviceType](doc:assigndevicetype)",
    "11-1": "Access JSON Web Token (ManageUser)",
    "11-2": "PUT /user/{id}/devicetype/{deviceTypeId}",
    "11-3": "Associates device type with the user.",
    "12-0": "[unassignDeviceType](doc:unassigndevicetype)",
    "12-1": "Access JSON Web Token (ManageUser)",
    "12-2": "DELETE /user/{id}/devicetype/{deviceTypeId}",
    "12-3": "Removes association between device type and user.",
    "13-0": "[getDeviceTypes](doc:getdevicetypes)",
    "13-1": "Access JSON Web Token (ManageUser)",
    "13-2": "GET /user/{id}/devicetype",
    "13-3": "Gets information about all user/device type associations.",
    "14-0": "[allowAllDeviceTypes](doc:allowalldevicetypes)",
    "14-1": "Access JSON Web Token (ManageUser)",
    "14-2": "PUT /user/{id}/devicetype/all",
    "14-3": "Allows all device types for user.",
    "15-0": "[disallowAllDeviceTypes](doc:disallowalldevicetypes)",
    "15-1": "Access JSON Web Token (ManageUser)",
    "15-2": "DELETE /user/{id}/devicetype/all",
    "15-3": "Disallows all device types for user."
  },
  "cols": 4,
  "rows": 16,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Resource Representation

```text
{
    "id": {integer},
    "login": {string},
    "role": {integer},
    "status": {integer},
    "lastLogin": {datetime},
    "data": {object},
    "introReviewed": {boolean}
}
```

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "id",
    "0-1": "integer",
    "0-2": "User identifier.",
    "1-0": "login",
    "1-1": "string",
    "1-2": "User login using during authentication.",
    "2-0": "role",
    "2-1": "integer",
    "2-2": "User role. Available values:  \n0: Administrator role  \n1: Client role",
    "3-0": "status",
    "3-1": "integer",
    "3-2": "User status. Available values:  \n0: The user is active  \n1: The user has been locked out due to invalid login attempts  \n2: The user has been disabled",
    "4-0": "lastLogin",
    "4-1": "datetime",
    "4-2": "User last login timestamp (UTC).",
    "5-0": "data",
    "5-1": "object",
    "5-2": "User data, a JSON object with an arbitrary structure.",
    "6-0": "introReviewed",
    "6-1": "boolean",
    "6-2": "Indicates if user reviewed an intro."
  },
  "cols": 3,
  "rows": 7,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]
