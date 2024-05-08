.. _backup_link: (https://answerhub.nagios.com/support/s/article/Migrating-Nagios-XI-2024-to-a-different-Server-d715ec94#:~:text=To%20restore%20a%20backup%20of%20your%20Nagios%20XI,to%20copy%20the.tar.gz%20file%20to%20the%20%2Fstore%2Fbackups%2Fnagiosxi%2F%20directory.)

Migrate 2024 Nagios to New Server
*********************************************

Backup CLI
#############

.. code-block:: console
    /usr/local/nagiosxi/scripts/restore_xi.sh </full/path/to/backupfile.tar.gz>
    /usr/local/nagiosxi/scripts/restore_xi.sh /store/backups/nagiosxi/1279411912.tar.gz

Change IP
###################

* Navigate to **Admin > System Config > System Settings** and ensure the Program URL and External URL are correct
* Navigate to **Administration > System Config > License Information** and ensure the server is licensed
* Reconfigure and agents/clients like NRPE or NSClient++ to allow the new IP address to connect

Changed OS Version / Architecture / Family
################################################

.. code-block:: console

    cd /tmp/
    wget https://assets.nagios.com/downloads/nagiosxi/scripts/restore_repair.sh
    chmod +x restore_repair.sh
    ./restore_repair.sh