troubleshooting
******************************

nagiosxi SQL Error [ndoutils: Table './nagios/nagios_hoststatus' is marked as crashed and should be repaired
##################################################################################################################

.. code-block:: console

    cat /usr/local/nagiosxi/etc/xi-sys.cfg
        mysqlpass=<password>
    mysql -u root -p
    USE nagios;
    REPAIR TABLE nagios_hoststatus;
    SHOW TABLE STATUS LIKE 'nagios_hoststatus';
    EXIT;
    systemctl restart nagios httpd

Error: (!log_opts) Could not complete SSL handshake with IP: : dh key too small
########################################################################################

Fix
+++++++++++++
upgrade nrpe on the host