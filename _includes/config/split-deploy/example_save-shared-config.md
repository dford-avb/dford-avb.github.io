1.  Log in to your development system as, or switch to, the {% glossarytooltip 5e7de323-626b-4d1b-a7e5-c8d13a92c5d3 %}Openmage file system owner{% endglossarytooltip %}.

1.  Enter the following commands in the order shown:

    ```bash
    cd <Openmage root dir>
    php bin/openmage app:config:dump
    ```

    For example, if Openmage is installed in `/var/www/html/openmage2`, enter:

    ```bash
    cd /var/www/html/openmage2
    php bin/openmage app:config:dump
    ```

1.  If you use Git, enter the following command to confirm that `app/etc/config.php` was updated:

    ```bash
    git status
    ```

    You should see output similar to the following:

    ```terminal
    On branch m2.2_deploy
    Changed but not updated:
      (use "git add &lt;file>..." to update what will be committed)
      (use "git checkout -- &lt;file>..." to discard changes in working directory)
           modified:   app/etc/config.php
    ```

    {:.bs-callout .bs-callout-warning}
    Do _not_ submit changes to the `generated`, `pub/media`, or `pub/static` directories to source control. You'll generate those files on your build system. The production system likely has code, themes, and so on that aren't ready to use on production.

1.  Check in your changes to `app/etc/config.php` only to source control.

    The Git command follows:

    ```bash
    git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
    ```
