---
title: "DeviceHive Playground"
slug: "about-playground"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 11:57:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2018 14:53:08 GMT+0000 (Coordinated Universal Time)"
---
At DeviceHive, we offer a basic playground, available at <https://playground.devicehive.com/>

## First Steps

Playground is by far the easiest way to start your IoT project:

1. Create an account. OAuth authorization is supported via Google+, Facebook and Github.

2. After sign-in, copy your Access-JWT and API URL

3. Confirm that your playground works by submitting a request similar to the following one (replace TOKEN with authentication token info from playground page):

```curl
curl -X GET -H 'Content-Type: application/json' -H 'Authorization: Bearer TOKEN' "https://playground.devicehive.com/api/rest/network"
```

4. Explore DeviceHive APIs through admin console - your personalized link is available via Playground.

## Default Network

Note that every user upon logging into Playground gets a default network assigned. This network name will look like "Network ABCDEF for ([username@example.com](mailto:username@example.com))". This name will be obligatory for the default network for this user.  
Practically, this means that in case this default network is renamed by administrator, it will discontinue being default.  
Instead, a new network with a new ID will be created, and named exactly as the original default network was. This new network with the original name will become default for the user.

## What Else is There?

Playground provides you with information needed to get access to your DeviceHive server hosted on our cloud. You can see:

- your API URL;
- your Access and Refresh JSON Web Tokens (JWTs);
- your automatically generated default network name and all non-default network IDs, if any;
- link to Admin Console;
- link to Dashboard;
- link to Swagger API Console;
- sample code to create your first device by simply executing it in your Terminal.
