---
title: "Network"
slug: "network"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 12:30:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jan 09 2018 14:59:15 GMT+0000 (Coordinated Universal Time)"
---
Represents a network, an isolated area where devices reside.

## Methods

[block:parameters]
{
  "data": {
    "h-0": "Method",
    "h-1": "Authorization",
    "h-2": "Uri",
    "h-3": "Description",
    "0-0": "[list](doc:list-1)",
    "0-1": "Access JSON Web Token (GetNetwork)",
    "0-2": "GET /network",
    "0-3": "Gets list of device networks.  \nThe result list is limited to networks the client has access to.",
    "1-0": "[count](doc:count-1)",
    "1-1": "Access JSON Web Token (GetNetwork)",
    "1-2": "GET /network/count",
    "1-3": "Gets count of networks.",
    "2-0": "[get](doc:get-5)",
    "2-1": "Access JSON Web Token (GetNetwork)",
    "2-2": "GET /network/{id}",
    "2-3": "Gets information about device network and its devices.",
    "3-0": "[insert](doc:insert-2)",
    "3-1": "Access JSON Web Token (ManageNetwork)",
    "3-2": "POST /network",
    "3-3": "Creates new device network.",
    "4-0": "[update](doc:update-1)",
    "4-1": "Access JSON Web Token (ManageNetwork)",
    "4-2": "PUT /network/{id}",
    "4-3": "Updates an existing device network.",
    "5-0": "[delete](doc:delete-2)",
    "5-1": "Access JSON Web Token (ManageNetwork)",
    "5-2": "DELETE /network/{id}",
    "5-3": "Deletes an existing device network."
  },
  "cols": 4,
  "rows": 6,
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
    "name": {string},
    "description": {string}
}
```

| Property Name | Type    | Description          |
| :------------ | :------ | :------------------- |
| id            | integer | Network identifier   |
| name          | string  | Network display name |
| description   | string  | Network description  |
