---
layout: m1x
title: nginx configuration
---

## Install nginx   {#instgde-pre-nginx-install}

We support nginx version 1.7.x. Installing the nginx software is beyond the scope of this guide. You can refer to a resource like the following:

*	[nginx wiki](https://www.nginx.com/resources/wiki/start/topics/tutorials/install/){: }
*	[How To Install Nginx on Ubuntu 14.04 LTS (digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-14-04-lts){: }
*	[How To Install Nginx on CentOS 6 (digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-centos-6-with-yum){: }

## nginx security setting   {#inst-pre-nginx-secy}

[Byte.nl](https://www.byte.nl/){: } recently reported that some misconfigured Openmage sites using the nginx web server software are vulnerable to attacks. The misconfiguration allows outside access to Openmage cache files. The cache files have predictable names and can contain sensitive information, including Openmage database passwords. This information can be used to obtain access to an installation and customer information.

To avoid this issue, you can use [this nginx configuration](https://gist.github.com/gwillem/cd5ae6845fa33aa0d481){: } provided by Willem de Groot.

We also recommend you review the [Openmage Security Best Practices](http://merch.docs.openmage.com/ee/user_guide/Openmage_Enterprise_Edition_User_Guide.html){: }.

Additionally, you can also check your site for other security vulnerabilities at [http://magereport.com](http://magereport.com){: }. This is a Openmage community project that is not affiliated with Openmage.