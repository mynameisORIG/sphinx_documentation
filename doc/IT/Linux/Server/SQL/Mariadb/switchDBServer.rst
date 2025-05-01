Switching from old Mariadb server to a new Mariadb server
*******************************************************************

Prepare Old Server
###########################

Ensure all data is consistent
+++++++++++++++++++++++++++++++++++++++++

Stop any appilcations (e.g Wordpress) that write to the database to avoid data changes during migration.

Or, lock the database in read-only mode (optional for replication use).

.. code-block:: console

    systemctl stop mariadb

Backup all databases
+++++++++++++++++++++++++++

The code below creates a full mariadb backup dump of all databases

.. code-block:: console

    mysqldump -u root -p --all-databases --routines --events --triggers --flush-privileges > /tmp/full_mariadb_backup.sql

The code below creates a mariadb backup dump of databases you choose

.. code-block:: console

    mysqldump -u root -p --databases app_db1 app_db2 wordpress_db --routines --events --triggers --flush-privileges > /tmp/filtered_mariadb_backup.sql

You would them dump the file to the new server

.. code-block:: console

    scp /tmp/full_mariadb_backup.sql user@newserver:/tmp/

Setup New Server
########################

Install Packages
+++++++++++++++++++++++++

.. code-block:: console

    sudo dnf install mariadb-server mariadb mariadb-libs mariadb-connector-c mariadb-connector-c-config

systemd service
++++++++++++++++++++

.. code-block:: console

    systemctl enable mariadb --now

Import the Data
######################

.. code-block:: console

    mysql -u root -p < /tmp/full_mariadb_backup.sql

Test the New Server
######################

.. code-block:: console

    mysql -u root -p -e "SHOW DATABASES;"
    mysql -u root -p -e "SELECT User, Host FROM mysql.user;"
