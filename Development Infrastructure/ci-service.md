---
title: "CI service"
slug: "ci-service"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Nov 21 2017 11:14:23 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 28 2017 08:44:57 GMT+0000 (Coordinated Universal Time)"
---
Link: <https://ci.devicehive.com/blue/>

Service uses "devicehive-ci-bot" user for privileged operations on GitHub repositories.

Currently Jenkins monitors and builds following repositories:

- devicehive-java-server
- devicehive-proxy
- devicehive-ws-kafka-proxy

# Authorization

Users of GitHub 'devicehive' organization can view projects and start builds.

# Connecting a new repository

1. Edit filter in Jenkins settings
2. Setup hook in GitHub repository: "Settings->Integration & services->Add service->Jenkins (GitHub plugin)", Jenkins hook url "<https://ci.devicehive.com/github-webhook/">. Click "Add service"
3. Optionally run "Scan organization now" in Jenkins UI.
