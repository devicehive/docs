---
title: "Running Docker on C.H.I.P."
slug: "running-docker-on-chip"
excerpt: "Tutorial on building Docker enabled kernel for $9 computer."
hidden: true
metadata:
  image: []
  robots: "index"
createdAt: "Tue Mar 22 2016 21:21:55 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---

## What is Docker?

[Docker](http://docker.io) is an open platform to ship and deploy distributed applications in an isolated way using containers.  
It's getting popularity among developers and enterprises for simplicity and agility of packaging applications and components of any complexity into simple and approachable format - container.

[block:image]
{
"images": [
{
"image": [
"images/BSt4OSeTQ2eYYdTEeuT0_docker.png",
"docker.png",
"1650"
],
"sizing": "80"
}
]
}
[/block]

## What is C.H.I.P.?

[C.H.I.P.](http://getchip.com/pages/chip) - world's first $9 computer as it states.  
Basically a tiny ARM computer that has 4GB of storage, 512MB RAM, WiFi and Bluetooth LE on board. Which makes it perfect for small hacking projects and demos.

[block:image]
{
"images": [
{
"image": [
"images/ym18YJCcSnW0wWwkGDMz_chip1.jpg",
"chip1.jpg",
"1200"
],
"sizing": "80"
}
]
}
[/block]

## Why?

This article is one of the series that will cover a new version of DeviceHive IoT Toolkit built on Docker containers. In the series we are going to cover building, packaging, distribution and deployment of docker containers on a wide range of x86 and ARM devices. So supporting C.H.I.P. for these IoT demos is a big plus. and this article should get your C.H.I.P. for the series.

## What is needed

We are going to use Docker ARM distribution provided by [Hypriot](http://blog.hypriot.com/) team. But in order to be installed docker requires specific features of Linux Kernel to be enabled. To know which ones are need one can use the following command:

```shell
# check current kernel settings
curl -L https://raw.githubusercontent.com/docker/docker/master/contrib/check-config.sh | /bin/bash

# check kernel settings in .config file
curl -L https://raw.githubusercontent.com/docker/docker/master/contrib/check-config.sh | /bin/bash /dev/stdin .config
```

What we need is `Generally Necessary` features and some Storage Drivers to be enabled. Preferably `aufs`.  
To enable these features we need to recompile kernel with updated .config file.  
The slow and easy way to do it on C.H.I.P. itself. But it can be also done on VM.  
This tutorial will cover first approach using this kindly provided guide [HOW-TO compile Chip's Linux kernel and modules on Chip itself](http://www.raspibo.org/wiki/index.php/HOW-TO_compile_Chip%27s_Linux_kernel_and_modules_on_Chip_itself).

## Building Kernel

Follow the guide and make sure after `make menuconfig` command your .config file passes required checks by `check-config.sh` script above.  
Here's the one I used for my build: [.config](https://gist.github.com/demon-xxi/4e3bf6c83dd79c7a15a3).

```shell Results of running check-config.sh
info: reading kernel config from /boot/config-4.3.0rd235-gfbe7da8-dirty ...

Generally Necessary:
- cgroup hierarchy: properly mounted [/sys/fs/cgroup]
- CONFIG_NAMESPACES: enabled
- CONFIG_NET_NS: enabled
- CONFIG_PID_NS: enabled
- CONFIG_IPC_NS: enabled
- CONFIG_UTS_NS: enabled
- CONFIG_DEVPTS_MULTIPLE_INSTANCES: enabled
- CONFIG_CGROUPS: enabled
- CONFIG_CGROUP_CPUACCT: enabled
- CONFIG_CGROUP_DEVICE: enabled
- CONFIG_CGROUP_FREEZER: enabled
- CONFIG_CGROUP_SCHED: enabled
- CONFIG_CPUSETS: enabled
- CONFIG_MEMCG: enabled
- CONFIG_KEYS: enabled
- CONFIG_MACVLAN: enabled (as module)
- CONFIG_VETH: enabled (as module)
- CONFIG_BRIDGE: enabled (as module)
- CONFIG_BRIDGE_NETFILTER: enabled (as module)
- CONFIG_NF_NAT_IPV4: enabled (as module)
- CONFIG_IP_NF_FILTER: enabled
- CONFIG_IP_NF_TARGET_MASQUERADE: enabled (as module)
- CONFIG_NETFILTER_XT_MATCH_ADDRTYPE: enabled (as module)
- CONFIG_NETFILTER_XT_MATCH_CONNTRACK: enabled (as module)
- CONFIG_NF_NAT: enabled (as module)
- CONFIG_NF_NAT_NEEDED: enabled
- CONFIG_POSIX_MQUEUE: enabled

Optional Features:
- CONFIG_USER_NS: enabled
- CONFIG_SECCOMP: enabled
- CONFIG_CGROUP_PIDS: enabled
- CONFIG_MEMCG_KMEM: enabled
- CONFIG_MEMCG_SWAP: enabled
- CONFIG_MEMCG_SWAP_ENABLED: enabled
- CONFIG_BLK_CGROUP: enabled
- CONFIG_IOSCHED_CFQ: enabled
- CONFIG_BLK_DEV_THROTTLING: enabled
- CONFIG_CGROUP_PERF: enabled
- CONFIG_CGROUP_HUGETLB: missing
- CONFIG_NET_CLS_CGROUP: missing
- CONFIG_CGROUP_NET_PRIO: enabled
- CONFIG_CFS_BANDWIDTH: enabled
- CONFIG_FAIR_GROUP_SCHED: enabled
- CONFIG_RT_GROUP_SCHED: enabled
- CONFIG_EXT3_FS: enabled
- CONFIG_EXT3_FS_XATTR: missing
- CONFIG_EXT3_FS_POSIX_ACL: enabled
- CONFIG_EXT3_FS_SECURITY: enabled
    (enable these ext3 configs if you are using ext3 as backing filesystem)
- CONFIG_EXT4_FS: enabled
- CONFIG_EXT4_FS_POSIX_ACL: enabled
- CONFIG_EXT4_FS_SECURITY: enabled
- Storage Drivers:
  - "aufs":
    - CONFIG_AUFS_FS: missing
  - "btrfs":
    - CONFIG_BTRFS_FS: enabled
  - "devicemapper":
    - CONFIG_BLK_DEV_DM: missing
    - CONFIG_DM_THIN_PROVISIONING: missing
  - "overlay":
    - CONFIG_OVERLAY_FS: enabled
  - "zfs":
    - /dev/zfs: missing
    - zfs command: missing
    - zpool command: missing
```

Follow the rest of tutorial by building kernel and replacing existing one with the new build. Make sure you have enough time and good power source for your C.H.I.P. as compiling kernel on this tiny device take hours.

## Installing Docker

Go to [Hypriot Downloads](http://blog.hypriot.com/downloads/#hypriot-docker-debian-packages-for-raspberry-pi:2a4af035d9e12b64c084b5e7cfb2c420) page and choose the docker version that you need.  
I've tried 1.9.1 and 1.10.3 and they both worked. Download and install the one you need:

```shell
wget https://downloads.hypriot.com/docker-hypriot_1.10.3-1_armhf.deb
sudo dpkg -i docker-hypriot_1.10.3-1_armhf.deb
```

Start Docker:

```shell
sudo docker daemon
```

That's it. You should now have docker engine running on C.H.I.P.!  
Now the hardest part - find _armhf_ compatible images to pull and run on docker.  
We are going to cover this in the next tutorial by installing DeviceHive IoT toolkit on C.H.I.P.

But as a quick test you can run this armhf-alpine container:

```shell
sudo docker run container4armhf/armhf-alpine:3.3 uname -a; echo Hello Docker!
```
