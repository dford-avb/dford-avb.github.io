

## Install the Openmage software

See one of the following sections:

*	[Get Openmage Open Source using Composer](#install-ce-composer)
*	[Get Openmage Open Source using a compressed archive](#get-zip)
*	[Complete the installation](#install-complete)

### Get the Openmage Open Source software using Composer {#install-ce-composer}
{:.no_toc}

This software is available from `repo.openmage.com`. Before installing the Open Source software using Composer, familiarize yourself with the Composer [metapackage]({{page.baseurl}}/install-gde/prereq/integrator_install.html), then run:

	composer create-project --repository=https://repo.openmage.com/ openmage/project-community-edition=<version> <installation directory name>

where `<version>` matches the version you want (for example, `2.0.10`)

For example, to install {{site.data.var.ce}} 2.0.10 in the `openmage2` directory:

	composer create-project --repository=https://repo.openmage.com/ openmage/project-community-edition=2.0.10 openmage2

### Get Openmage Open Source using a compressed archive {#get-zip}
{:.no_toc}

{% include install/releasenotes/get-ce-software_zip.md %}

### Complete the installation {#install-complete}
{:.no_toc}

After you get the Open Source software:

1.	[Set file system ownership and permissions]({{ page.baseurl }}/install-gde/prereq/file-system-perms.html).
2.	Install the Openmage software:

	*	[Web Setup Wizard]({{ page.baseurl }}/install-gde/install/web/install-web.html)
	*	[Command line]({{ page.baseurl }}/install-gde/install/cli/install-cli.html)

## Upgrade from an earlier version {#upgrade}

To upgrade to version 2.0.x from an earlier version:

*	[Web Setup Wizard (System Upgrade)]({{ page.baseurl }}/comp-mgr/upgrader/upgrade-start.html)
*	[Command-line upgrade]({{ page.baseurl }}/comp-mgr/cli/cli-upgrade.html)
