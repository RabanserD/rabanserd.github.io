---
layout: post
title:  "How to enable auto updates on Rocky Linux 9 w/ dnf-automatic"
date:   2023-02-01 12:00:00 +0200
tags: linux
author: "Daniel Rabanser "
comments: true
---
This post will show you how to enable automatic system updates for your CentOS 9 / RHEL 9 / Rocky 9 system.
<!--excerpt-->  

<br>

### Update your system
It might be a good idea to update your system before installing something. Kind of ironic isn't it? We'll do it anyway.
```
[root@rocky ~]# yum update
```

<br>

### Install dnf-automatic
```
[root@rocky ~]# yum install dnf-automatic
```

<br>

### Configure dnf-automatic
This will enable daily updates
```
[root@rocky ~]# vi /etc/dnf/automatic.conf
```
```
apply_updates = yes                  
```

<br>

### Set a schedule for updates
By default updates are installed once a day at 06:00 with a random delay of 60m, I suggest changing that to 04:00 with a delay of 15m
```
[root@rocky ~]# systemctl edit -f dnf-automatic-install.timer
```
```
# [Timer]
# OnCalendar=*-*-* 4:00
# RandomizedDelaySec=10m
# Persistent=true
                 
```

<br>

### Start dnf-automatic
Lastly start dnf-automatic and enable it to start automatically at boot time
```
[root@rocky ~]# systemctl enable dnf-automatic.timer
[root@rocky ~]# systemctl start dnf-automatic.timer
```
