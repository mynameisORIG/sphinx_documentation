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

System Profile build failed
####################################

Error
++++++++++++++

.. code-block:: console
    
    PROFILE BUILD FAILED
    Array
    (
    )
    CODE: 1

Fix
++++++++++++

Source: https://support.nagios.com/kb/article/nagios-xi-profile-build-failed-533.html

Download nagios XI installation files to your server

.. code-block:: console
    
    cd /tmp
    wget https://assets.nagios.com/downloads/nagiosxi/5/xi-5.6.3.tar.gz

Extract the name of the download files

.. code-block:: console

    tar xzf xi-5.6.3.tar.gz nagiosxi/nagiosxi/nagiosxi.sudoers --strip-components 2

This will have extracted a file called nagiosxi.sudoers and this file contains all the correct entries.

Run all these commands to fix your /etc/sudoers file to make sure it has all the correct entries:

.. code-block:: console

    grep -v NAGIOSXI /etc/sudoers > /etc/sudoers.new
    mv -f /etc/sudoers.new /etc/sudoers
    rm -rf /etc/sudoers.d/nagiosxi
    sed -i 's/^Defaults    requiretty/#Defaults    requiretty/g' /etc/sudoers
    cat /tmp/nagiosxi.sudoers >> /etc/sudoers
    chmod 440 /etc/sudoers

Notes
+++++++++++++++

This can also fix some issues within your Admin -> System Component Status Components like:

* Monitoring Engine
* Performance Grapher
    