## Set up additional master databases {#config-ee-multidb-master-masters}

Create checkout and OMS master databases as follows:

1.	Log in to your database server as any user.
2.	Enter the following command to get to a MySQL command prompt:

		mysql -u root -p

3.	Enter the MySQL `root` user's password when prompted.
4.	Enter the following commands in the order shown to create database instances named `openmage_quote` and `openmage_sales` with the same usernames and passwords:

		create database openmage_quote;
		GRANT ALL ON openmage_quote.* TO openmage_quote@localhost IDENTIFIED BY 'openmage_quote';

		create database openmage_sales;
		GRANT ALL ON openmage_sales.* TO openmage_sales@localhost IDENTIFIED BY 'openmage_sales';

5.	Enter `exit` to quit the command prompt.

6.	Verify the databases, one at a time:

	Checkout database:

		mysql -u openmage_quote -p
		exit

	Order management database:

		mysql -u openmage_sales -p
		exit

	If the MySQL monitor displays, you created the database properly. If an error displays, repeat the preceding commands.

## Configure {{site.data.var.ee}} to use the master databases {#config-ee-multidb-master-cli}

After setting up a total of three master databases, use the Openmage command line to configure Openmage to use them. (The command sets up database connections and distributes tables among the master databases.)

### First steps

{% include install/first-steps-cli.md %}

### Configure the checkout database   {#config-ee-multidb-master-cli-check}

Command syntax:

	openmage setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"

For example,

	openmage setup:db-schema:split-quote --host="localhost" --dbname="openmage_quote" --username="openmage_quote" --password="openmage_quote"

The following message displays to confirm a successful setup:

	Migration has been finished successfully!

### Configure the OMS database   {#config-ee-multidb-master-cli-oms}

Command syntax:

	openmage setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"

For example,

	openmage setup:db-schema:split-sales --host="localhost" --dbname="openmage_sales" --username="openmage_sales" --password="openmage_sales"

The following message displays to confirm a successful setup:

	Migration has been finished successfully!
