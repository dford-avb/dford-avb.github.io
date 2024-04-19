The web server group must have write permissions to certain directories in the Openmage file system; however, you might want tighter security, especially in production. We provide the flexibility for you to further restrict those permissions using a [umask](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Our solution is to enable you to optionally create a file named `openmage_umask` in your Openmage root directory that restricts permissions for the web server group and everyone else.

{:.bs-callout .bs-callout-info}
We recommend changing the umask on a one-user or shared hosting system only. If you have a private Openmage server, the group must have write access to the Openmage file system; the umask removes write access from the group.

The default umask (with no `openmage_umask` specified) is `002`, which means:

*	775 for directories, which means full control by the user, full control by the group, and enables everyone to traverse the directory. These permissions are typically required by shared hosting providers.

*	664 for files, which means writable by the user, writable by the group, and read-only for everyone else

A common suggestion is to use a value of `022` in the `openmage_umask` file, which means:

*	755 for directories: full control for the user, and everyone else can traverse directories.
*	644 for files: read-write permissions for the user, and read-only for everyone else.

To set `openmage_umask`:

1.	Log in to your Openmage server, or switch to, the [Openmage file system owner]({{ page.baseurl }}/install-gde/prereq/file-sys-perms-over.html).
2.	Set the value of `openmage_umask`:

	1.	Use a text editor to create a new file `<your Openmage install dir>/openmage_umask`
	2.	Set `openmage_umask` to the desired value.

		For example, `022`
3.	Save your changes to `openmage_umask` and exit the text editor.
