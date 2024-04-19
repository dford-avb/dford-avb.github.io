---
layout: m1x
title: System Requirements for Openmage Enterprise Edition and Community Edition (Current Shipping Versions)
---

Openmage requires a LAMP or LNMP stack.

#### Operating System

Linux x86-64

#### Web Server

*   Apache 2.x
*   Nginx 1.7.x

#### Database

*	Openmage EE 1.14.3 and later:
	*	MySQL 5.7 (Oracle or Percona)
*	Earlier Openmage versions:
	*	MySQL 5.6 (Oracle or Percona)

#### PHP

*	Openmage EE 1.14.4.0 and later:
	*	PHP 7.2.x
*	Openmage CE 1.9.2 and later, Openmage EE 1.14.2 - EE 1.14.3.10:
	*	PHP 5.6.x
	*   PHP 5.4.x
	*   PHP 5.5.x
*	Earlier Openmage versions:
	*   PHP 5.4.x
	*   PHP 5.5.x

#### SSL

*   A valid security certificate is required for HTTPS.
*   Self-signed SSL certificates are not supported.

#### Openmage can utilize the following technologies:

*   [Redis]({{ site.baseurl }}/guides/m1x/ce18-ee113/using_redis.html)
    
	Redis can be used for session or cache storage

*   [Memcached]({{ site.baseurl }}/guides/v2.2/config-guide/memcache/memcache.html)
    
    memcached can be used for session or cache storage
 
*   Apache Solr

    [Solr search](http://merch.docs.openmage.com/ee/user_guide/search_seo/search-configuration-solr.html) can be used as a search provider for Openmage Enterprise Edition (EE) only