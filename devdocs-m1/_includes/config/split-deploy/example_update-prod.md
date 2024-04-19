To update the production system:

1.	Log in to your production system as, or switch to, the {% glossarytooltip 5e7de323-626b-4d1b-a7e5-c8d13a92c5d3 %}Openmage file system owner{% endglossarytooltip %}.
2.	Start maintenance mode:

		cd <Openmage root dir>
		php bin/openmage maintenance:enable

	For additional options, such as the ability to set an IP address whitelist, see [`openmage maintenance:enable`]({{ page.baseurl }}/install-gde/install/cli/install-cli-subcommands-maint.html).
3.	If you use {{site.data.var.ee}}, stop queue workers. TBD
3.	Pull code from source control.

	The Git command follows:

		git pull mconfig m2.2_deploy
4.	Update the configuration:

		php bin/openmage app:config:import
5.	Clean the cache:

		php bin/openmage cache:clean
4.	End maintenance mode:

		php bin/openmage maintenance:disable
