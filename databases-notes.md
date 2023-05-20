# Databases commands and notes

## MySQL

To install MySQL on WSL:

1. Open your WSL terminal

2. Update your Ubuntu packages: `sudo apt update`

3. Once the packages have updated, install MySQL with: `sudo apt install mysql-server`

4. Confirm installation and get the version number: `mysql --version`

You may also want to run the included security script.

1. Start a MySQL server: `sudo /etc/init.d/mysql start`

2. Start the security script prompts: `sudo mysql_secure_installation`

The first prompt will ask whether you’d like to set up the Validate Password Plugin, which can be used to test the strength of your MySQL password. You will then set a password for the MySQL root user, decide whether or not to remove anonymous users, decide whether to allow the root user to login both locally and remotely, decide whether to remove the test database, and, lastly, decide whether to reload the privilege tables immediately.

To open the MySQL prompt, enter: `sudo mysql`

To see what databases you have available, in the MySQL prompt, enter: `SHOW DATABASES;`

To create a new database, enter: `CREATE DATABASE database_name;`

To delete a database, enter: `DROP DATABASE database_name;`

## PostgreSQL

To install PostgreSQL on WSL:

1. Open your WSL terminal

2. Update your Ubuntu packages: `sudo apt update`

3. Once the packages have updated, install PostgreSQL (and the -contrib package which has some helpful utilities) with: `sudo apt install postgresql postgresql-contrib`

4. Confirm installation and get the version number: `psql --version`

There are 3 commands you need to know once PostgreSQL is installed:

- `sudo service postgresql status` for checking the status of your database.

- `sudo service postgresql start` to start running your database.

- `sudo service postgresql stop` to stop running your database.

The default admin user, **postgres**, needs a password assigned in order to connect to a database. To set a password:

1. Enter the command: `sudo passwd postgres`

2. You will get a prompt to enter your new password.

3. Close and reopen your terminal.

To run PostgreSQL with [psql](https://www.postgresql.org/docs/current/app-psql.html) shell:

1. Start your postgres service: `sudo service postgresql start`

2. Connect to the postgres service and open the psql shell: `sudo -u postgres psql`

Once you have successfully entered the psql shell, you will see your command line change to look like this: `postgres=#`

**Note**: Alternatively, you can open the psql shell by switching to the postgres user with: `su - postgres` and then entering the command: `psql`.

To exit postgres=# enter: `\q` or use the shortcut key: Ctrl+D

## MongoDB

See [Install MongoDB Community Edition on Ubuntu](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/)

Use MongoDB Atlas, see https://www.mongodb.com/cloud/atlas/register

## MSSQL

To install SQL Server on WSL, follow this quickstart: [Install SQL Server and create a database on Ubuntu](https://learn.microsoft.com/en-us/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-ver16).

## Redis

To install Redis on WSL:

1. Open your WSL terminal

2. Update your Ubuntu packages: `sudo apt update`

3. Once the packages have updated, install Redis with: `sudo apt install redis-server`

4. Confirm installation and get the version number: `redis-server --version`

To start running your Redis server: `sudo service redis-server start`

To stop your Redis server: `sudo service redis-server stop`
