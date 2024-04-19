1.	Log in to the Openmage server as, or switch to, a user who has permissions to write to the Openmage file system. One way to do this is to [switch to the Openmage file system owner]({{ page.baseurl }}/install-gde/prereq/file-sys-perms-over.html).

	If you use the bash shell, you can also use the following syntax to switch to the Openmage file system owner and enter the command at the same time:

		su <Openmage file system owner> -s /bin/bash -c <command>

	If the Openmage file system owner does not allow logins you can do the following:

		sudo -u <Openmage file system owner>  <command>
2.	To run Openmage commands from any directory, add `<your Openmage install dir>/bin` to your system `PATH`.

	Because shells have differing syntax, consult a reference like [unix.stackexchange.com](http://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

	bash shell example for CentOS:

		export PATH=$PATH:/var/www/html/openmage2/bin

{:.bs-callout .bs-callout-info}
You can also run the commands in the following ways:
-   `cd <your Openmage install dir>/bin` and run them as `./openmage <command name>`
-   `php <your Openmage install dir>/bin/openmage <command name>`
-   `<your Openmage install dir>` is a subdirectory of your web server's docroot. [Need help locating the docroot?]({{ page.baseurl }}/install-gde/basics/basics_docroot.html)
