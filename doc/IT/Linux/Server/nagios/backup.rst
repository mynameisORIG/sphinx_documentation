[Backup](https://answerhub.nagios.com/support/s/article/Backing-Up-and-Restoring-Migrating-Nagios-XI-2024-b36feda0)
****************************************************************************************************************************

Backup Overview
####################

The backup script will save a copy of the following components of Nagios XI:

* Nagios Core files (/usr/local/nagios/)
* Nagios XI files (/usr/local/nagiosxi/)
* NagiosQL files (/var/www/html/nagiosql/ and /etc/nagiosql/)
  * These do not exist on fresh installs of Nagios XI 5.5 or newer
* MRTG files (/var/lib/mrtg/ and /etc/mrtg/)
* NRDP files (/usr/local/nrdp/)
* NagVis files (/usr/local/nagvis/)
* CRON files (in /var/spool/cron/apache)
* Apache config files (in /etc/httpd/conf.d/)
* logrotate config files (in /etc/logrotate.d/)
* MySQL databases (nagios, nagiosql, nagiosxi)
* PostgresQL database (nagiosxi)
  * Clean installs of Nagios XI from 5.x will have the nagiosxi database created in MySQL.
  * Upgraded installs will continue to use PostgresQL and the restore script will correctly identify this

The backup will be saved in the **/store/backups/nagiosxi** directory.

CLI
#########

.. code-block:: console
    
    /usr/local/nagiosxi/scripts/backup_xi.sh


