### Prerequisites

Openmage uses cron for two sets of tasks, and for each, cron can run with a different configuration:

*	PHP command-line configuration: The general cron job that reindexes indexers, generates e-mails, generates the sitemap, and so on.

	You can find the command-line configuration using the command `php --ini`.
*	Web server PHP plug-in configuration: Two other cron jobs are used by the [Component Manager and System Upgrade utilities]({{ page.baseurl }}/comp-mgr/bk-compman-upgrade-guide.html).

	You can find the web server plug-in configuration using [`phpinfo.php`]({{ page.baseurl }}/install-gde/prereq/optional.html#install-optional-phpinfo).

{:.bs-callout .bs-callout-warning}
*	To avoid issues during installation and upgrade, we strongly recommend you apply the same PHP settings to both the PHP command-line configuration and to the PHP web server plug-in's configuration. For more information, see [Required PHP settings]({{ page.baseurl }}/install-gde/prereq/php-settings.html).
*	In a multi-node system, crontab can run on only one node. This applies to you only if you set up more than one webnode for reasons related to performance or scalability.

#### Find the PHP binary and php.ini path

To display the path to your PHP binary, enter

	which php

A sample result follows:

	/usr/bin/php

#### Create the cron job

To create a cron job for the Openmage file system owner, enter the following command as a user with `root` privileges:

	crontab -u <Openmage file system owner username> -e

For example,

	crontab -u openmage_user -e

A text editor displays. (You might need to choose a text editor first.)

```terminal
* * * * * <path to php binary> <openmage install dir>/bin/openmage cron:run | grep -v "Ran jobs by schedule" >> <openmage install dir>/var/log/openmage.cron.log
* * * * * <path to php binary> <openmage install dir>/update/cron.php >> <openmage install dir>/var/log/update.cron.log
* * * * * <path to php binary> <openmage install dir>/bin/openmage setup:cron:run >> <openmage install dir>/var/log/setup.cron.log</pre>
```

where

*	`<path to php binary>` is the absolute file system path to your PHP binary
*	`<openmage install dir>` is the directory in which you installed the Openmage software; for example, `/var/www`
*	`| grep -v "Ran jobs by schedule"` filters this message from the log, making any errors easier to spot

The first command (`openmage cron:run`) reindexes indexers, sends automated e-mails, generates the sitemap, and so on. Usually it's associated with the PHP command line `.ini` file. The other two commands are used by the Component Manager and System Upgrade.

{:.bs-callout .bs-callout-info}
If you're a contributing developer (that is, you [cloned the Openmage 2 GitHub repository]({{ page.baseurl }}/install-gde/prereq/dev_install.html)), only the first line applies to you. See the examples that follow for details.

**Example 1:** Everyone except contributing developers

For example, if the PHP binary is located in `/usr/bin`, you installed Openmage in `/var/www/openmage2`, enter

Example:

```terminal
* * * * * /usr/bin/php /var/www/openmage2/bin/openmage cron:run | grep -v "Ran jobs by schedule" >> /var/www/openmage2/var/log/openmage.cron.log
* * * * * /usr/bin/php /var/www/openmage2/update/cron.php >> /var/www/openmage2/var/log/update.cron.log
* * * * * /usr/bin/php /var/www/openmage2/bin/openmage setup:cron:run >> /var/www/openmage2/var/log/setup.cron.log
```

**Example 2:** Contributing developers only (that is, you cloned the Openmage 2 GitHub repository):

```terminal
* * * * * /usr/bin/php /var/www/openmage2/bin/openmage cron:run | grep -v "Ran jobs by schedule" >> /var/www/openmage2/var/log/openmage.cron.log
```

The preceding works for contributing developers because if you cloned the GitHub repository you don't have an `update` directory and errors result if you run `openmage setup:cron:run`. These cron jobs work in the Web Setup Wizard, which contributing developers cannot use for installing or updating the Openmage application or components.

Save your changes to the crontab and exit the editor.
