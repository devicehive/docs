---
title: "DeviceHive Cloud Connector"
slug: "cloud-connector"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jul 24 2015 05:48:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Once you [started](doc:iot-toolkit-overview) devicehive-cloud service, you can connect to device hive cloud dbus wrapper

```go
type dbusWrapper struct {
	conn        *dbus.Conn
	path, iface string
}

func NewdbusWrapper(path string, iface string) (*dbusWrapper, error) {
	d := new(dbusWrapper)

	conn, err := dbus.SystemBus()
	if err != nil {
		return nil, err
	}

	d.conn = conn
	d.path = path
	d.iface = iface

	return d, nil
}

func (d *dbusWrapper) call(name string, args ...interface{}) *dbus.Call {
	c := d.conn.Object(d.iface, dbus.ObjectPath(d.path)).Call(d.iface+"."+name, 0, args...)

	if c.Err != nil {
		log.Printf("Error calling %s: %s", name, c.Err)
	}

	return c
}
```

with the busName "com.devicehive.cloud" and path "/com/devicehive/cloud":

```go
cloud, err := NewdbusWrapper("/com/devicehive/cloud", "com.devicehive.cloud")
```

As far you remember, during starting cloud service, you specify configuration file with deviceId and deviceName. As result, devicehive-cloud service represents command interface to that device. So, you can send notifications to that device and update commands with the following functions:

**UpdateCommand(commandId int, status string, result string)**  
as result, cloud service will send "command/update" request to DH server for specified commandId with status and result (JSON as string)

**SendNotification(name string, parameters string, priority int)**  
which corresponds to "notification/insert" DH server command (parameters should be JSON as string). Priority = 1 would work fine.

example which sends notification each second you can find below:

```go
package main

import (
	"encoding/json"
	"github.com/godbus/dbus"
	"github.com/shirou/gopsutil/cpu"
	"github.com/shirou/gopsutil/mem"
	"log"
	"os"
	"time"
)

type dbusWrapper struct {
	conn        *dbus.Conn
	path, iface string
}

func NewdbusWrapper(path string, iface string) (*dbusWrapper, error) {
	d := new(dbusWrapper)

	conn, err := dbus.SystemBus()
	if err != nil {
		return nil, err
	}

	d.conn = conn
	d.path = path
	d.iface = iface

	return d, nil
}

func (d *dbusWrapper) call(name string, args ...interface{}) *dbus.Call {
	c := d.conn.Object(d.iface, dbus.ObjectPath(d.path)).Call(d.iface+"."+name, 0, args...)

	if c.Err != nil {
		log.Printf("Error calling %s: %s", name, c.Err)
	}

	return c
}

func (d *dbusWrapper) SendNotification(name string, parameters interface{}) {
	b, _ := json.Marshal(parameters)
	d.call("SendNotification", name, string(b), uint64(1))
}

func main() {
	cloud, err := NewdbusWrapper("/com/devicehive/cloud", "com.devicehive.cloud")
	if err != nil {
		log.Panic(err)
	}

	h, _ := os.Hostname()

	for {
		time.Sleep(time.Second)
		c, err := cpu.CPUPercent(time.Second, false)
		if err != nil {
			log.Panic(err)
		}

		v, err := mem.VirtualMemory()
		if err != nil {
			log.Panic(err)
		}

		if len(c) > 0 {
			cloud.SendNotification("stats", map[string]interface{}{
				"cpu-usage":    c[0],
				"memory-total": v.Total,
				"memory-free":  v.Free,
				"name":         h,
			})
		}
	}
}
```
