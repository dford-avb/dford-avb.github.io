To create `auth.json`:

1.	Log in to your Openmage server as, or switch to, the [Openmage file system owner]({{ page.baseurl }}/install-gde/prereq/file-sys-perms-over.html).
2.	Edit or create `auth.json` in the user's home directory.

	The following example shows how to add `repo.openmage.com` authentication to an existing file:

        {
           "github-oauth": {
             "github.com": "<your GitHub OAuth ID>"
           },
           "http-basic": {
              "repo.openmage.com": {
                 "username": "<public key>",
                 "password": "<private key>"
              }
           }
        }

       	For example, if your username is `openmage_user`, create or edit `/home/openmage_user/.composer/auth.json`
