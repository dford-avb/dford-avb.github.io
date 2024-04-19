This section discusses how to install the Openmage software using a web-based wizard interface. To install Openmage from the command line, see [Install Openmage software using the command line]({{ page.baseurl }}/install-gde/install/cli/install-cli.html).

## Before you start your installation   {#instgde-install-prereq}

Before you begin, make sure that:

1.	Your system meets the requirements discussed in [Openmage System Requirements]({{ page.baseurl }}/install-gde/system-requirements.html).
2.	You completed all prerequisite tasks discussed in [Prerequisites]({{ page.baseurl }}/install-gde/prereq/prereq-overview.html).
4.	After you log in to the Openmage server, [switch to the Openmage file system owner]({{ page.baseurl }}/install-gde/prereq/file-sys-perms-over.html).

### Enabling and disabling modules   {#instgde-install-web-enable-mod}

The Setup Wizard enables you to enable or disable modules before you install the Openmage software. Before you do so, make sure you understand the following.

{% include install/enable-disable-modules.md %}

## Running the Setup Wizard   {#instgde-install-openmage-web}

The Setup Wizard is a multi-page wizard that enables you to go back and forward one page at a time. You *cannot* skip pages, and you must enter all required information on every page before you can proceed to the next page.

In the event of errors, you can run the installer again or you can return to a previous page to fix errors on that page.

### Getting started   {#instgde-install-openmage-web-step0}

To install the Openmage software using the Setup Wizard:

1.	Start a web browser.

2.	Enter the following URL in the browser's address or location bar:

		http://<Openmage host or IP>/<path to Openmage root>/setup

	For example, if the Openmage server's IP address is 192.0.2.10 and you installed Openmage 2 in the `openmage2/` directory relative to the web server's docroot, and you did not configure a Virtual Host, enter:

		http://192.0.2.10/openmage2/setup

3.	On the initial page, click **Agree and Set Up Openmage**.

4.	Continue with the following topics in the order presented to complete the installation.
