---
title: "Docker Hub and Docker Cloud"
slug: "docker-hub-and-docker-cloud"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Nov 28 2017 08:20:16 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 28 2017 08:44:12 GMT+0000 (Coordinated Universal Time)"
---
# Docker Hub repositories

DeviceHive project has two Docker Hub repositories:

1. Main [devicehive](hub.docker.com/r/devicehive/) that has all images
2. And [devicehiveci](hub.docker.com/r/devicehiveci/) repository with images built by our Jenkins CI

# Docker Cloud builds

Docker Cloud service was used before to build 'devicehive-java-server', 'devicehive-playground', 'devicehive-admin-console' and some other projects. But due to limits of this service, long build delays and build issues, our own build service was introduced and most of the builds are switched to Jenkins. Currently Docker Cloud builds only 'devicehive-playground' project.

# Docker Hub bots

Jenkins builds are published to Docker Hub by 'devicehiveci' user. It has full access to 'devicehiveci' repository and added to 'robots' group in 'devicehive' repo. In order to grant 'devicehiveci' user rights to publish images to 'devicehive' repo you need to add group 'robots' with 'Read & Write' permissions for each image.
