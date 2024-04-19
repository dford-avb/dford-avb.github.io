#### To create and transfer `config.local.php`:

1.  On your local workstation, find the integration server SSH URL.

    ```bash
    openmage-cloud environment:ssh --pipe
    ```

1.  Create the `config.local.php` file on the integration server.

    ```bash
    ssh server@ssh.openmagesite.cloud "php bin/openmage openmage-cloud:scd-dump"
    ```

1.  Change to the project root directory.

1.  Transfer the `config.local.php` file to your local workstation.

    ```bash
    rsync server@ssh.openmagesite.cloud:app/etc/config.local.php ./app/etc/config.local.php
    ```

1.  Test to ensure a successful transfer by importing the configuration file to your local environment.

    ```bash
    php bin/openmage app:config:import
    ```
