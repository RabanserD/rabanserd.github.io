---
layout: post
title:  "How to install PHP 7.3 on CentOS 7 /w Remi"
date:   2019-04-29 23:00:00 +0200
tags: linux web
author: "Daniel Rabanser "
comments: true
---
Most modern web applications require a modern version of PHP, since RHEL/CentOS comes with 5.4 those requirements can't always be met.
<!--excerpt-->  
To upgrade to a more recent version of PHP you have a few options. Depending on the environment you might choose one over another.

1. RHEL/CentOS Software Collections (SCL)
2. 3rd Party repository such as Remi

I'll go through the second approach, I might or might not do a SCL edition of this post (probably not).  
Remi provides a nice [configuration wizard](https://rpms.remirepo.net/wizard/) if you want to go for another distro/PHP version.

<br>

### Update your system
Get the latest updates for your CentOS server
```
[root@centos ~]# yum update
```

<br>

### Add the EPEL repo to your system
You'll need to have the EPEL repository installed.
```
[root@centos ~]# yum install epel-release
```

<br>

### Add the Remi repo to your system
PHP will be installed from this repository
```
[root@centos ~]# yum install http://rpms.remirepo.net/enterprise/remi-release-7.rpm
```

<br>

### Install yum-utils
Used to manage yum repositories
```
[root@centos ~]# yum install yum-utils
```

<br>

### Enable the remi-php73 repo
That will enable the installed repository
```
[root@centos ~]# yum-config-manager --enable remi-php73
```

<br>

### Upgrade PHP
This will upgrade PHP 5.4 to PHP 7.3
```
[root@centos ~]# yum update
```