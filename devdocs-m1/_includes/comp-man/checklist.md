Before you continue, to avoid errors during your installation or update, make sure you verify *all* of the following:

*	You set up a [Openmage file system owner](#openmage-owner-group) and shared that owner's group with the web server user group
*	Your [cron jobs](#openmage-cron) are set up and running
*	[File system permissions](#perms) are set properly

{:.bs-callout .bs-callout-warning}
Do not continue without performing these checks. Failure to do so could result in errors.

### Openmage file system owner and group {#openmage-owner-group}

The [Openmage file system owner]({{ page.baseurl }}/install-gde/prereq/file-sys-perms-over.html) group must have write access to Openmage directories and files.

### Cron jobs are running {#openmage-cron}

Openmage requires three cron jobs, all running as the [Openmage file system owner]({{ page.baseurl }}/install-gde/prereq/file-sys-perms-over.html).

To verify your cron jobs are set up properly, enter the following command as a user with `root` privileges:

	crontab -u <openmage file system owner> -l

For example, if your Openmage file system owner is named `openmage_user`, enter:

	crontab -u openmage_user -l

Results similar to the following should display:

	* * * * * /usr/bin/php /var/www/openmage2/bin/openmage cron:run | grep -v "Ran jobs by schedule" >> /var/www/openmage2/var/log/openmage.cron.log
	* * * * * /usr/bin/php /var/www/openmage2/update/cron.php >> /var/www/openmage2/var/log/update.cron.log
	* * * * * /usr/bin/php /var/www/openmage2/bin/openmage setup:cron:run >> /var/www/openmage2/var/log/setup.cron.log

Another symptom of cron not running is the following error in the Openmage Admin:

![cron isn't running]({{ site.baseurl }}/common/images/compman-cron-not-running.png){:width="500px"}

To see the error, you might need to click **System Messages** at the top of the window as follows:

![System Messages]({{ site.baseurl }}/common/images/compman_sys-messages.png)

For details, see [Set up cron]({{ page.baseurl }}/install-gde/install/post-install-config.html#post-install-cron).

### File system permissions {#perms}

For security reasons, Openmage requires certain permissions on the file system. Permissions are different from [*ownership*](#openmage-owner-group). Ownership determines *who* can perform actions on the file system; permissions determine *what* the user can do.

Directories in the Openmage file system must be writable by the [Openmage file system owner's]({{ page.baseurl }}/install-gde/prereq/file-sys-perms-over.html) group.

To verify your file system permissions are set properly, either log in to the Openmage server or use your hosting provider's file manager application.

For example, enter the following commands on a Linux system if the Openmage application is installed in `/var/www/html/openmage2`:

	ls -al /var/www/html/openmage2

A sample result follows:

{% highlight xml %}
total 1028
drwxrwx---. 12 openmage_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 openmage_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 openmage_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 openmage_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 openmage_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 openmage_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 openmage_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 openmage_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 openmage_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 openmage_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 openmage_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 openmage_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 openmage_user apache   6419 Apr 27 21:23 .htaccess.sample
-rw-rw----.  1 openmage_user apache   1358 Apr 27 21:23 index.php
drwxrwx---.  4 openmage_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 openmage_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 openmage_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 openmage_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 openmage_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 openmage_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 openmage_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 openmage_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 openmage_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 openmage_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 openmage_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 openmage_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 openmage_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 openmage_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 openmage_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 openmage_user apache   4096 Jun  7 07:53 vendor
{% endhighlight %}

In the preceding example, the Openmage file system owner is `openmage_user`. Directories in the Openmage file system have `drwxrwx---` permissions (775) and files have `-rw-rw-rw-` permissions (664).

To get more detailed information, you can optionally enter the following command:

	ls -al /var/www/html/openmage2/pub

Because Openmage deploys static file assets to subdirectories of `pub`, it's a good idea to verify permissions and ownership there as well.

For more information, see [File system permissions and ownership]({{ page.baseurl }}/install-gde/prereq/file-sys-perms-over.html).
