---
title: "Starting Freeboard"
slug: "starting-freeboard"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Jun 19 2017 13:09:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Freeboard can be started with

```text
open index.html
```

Or it can be started in nginx. For this add

```text
location /freeboard {
    sendfile on;
    root path/to/the/parent/of/freeboard/;
    index index.html;
}
```

to the server section of nginx.conf. [More details on github](https://github.com/devicehive/freeboard).
