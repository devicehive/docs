---
title: "Monitoring and alerting"
slug: "monitoring-and-alerting"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Nov 21 2017 13:50:17 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 06 2017 17:23:27 GMT+0000 (Coordinated Universal Time)"
---
Stack:

- ["Prometheus"](https://prometheus.devicehive.com/) for monitoring. User 'admin', for password ask Tatyana or Alexander.
- ["Alert Manager"](https://alertmanager.devicehive.com/) for sending alerts. User 'admin', for password ask Tatyana or Alexander.
- "Node Exporter" for Linux node metrics
- "Blackbox exporter" for testing REST API availability
- Additional "JMX Java agent" exporter added to Kafka container on dev.devicehive.com

# Configuration

Components are installed and configured by Ansible using playbooks from [devicehive-ops](https://github.com/devicehive/devicehive-ops) repository.
