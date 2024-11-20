Transferring clients from an old puppetserver to a new one
****************************************************************

Step 1: Backup certs on the old puppetserver
###################################################

You will need to backup the CA directory and the SSL directory

.. code-block:: console

    tar -czvf puppet_ca_backup.tar.gz /etc/puppetlabs/puppetserver/ca
    tar -czvf puppet_ssl_backup.tar.gz /etc/puppetlabs/puppet/ssl

Step 2: Transfer certs to the New Puppet Server
######################################################

**NOTE** This assumes you already transffered the .tar.gz files to the new server **NOTE**

You will first need to stop the puppetserver

.. code-block:: console

    systemctl stop puppetserver

You will then need to extract the .tar.gz files on the new server

.. code-block:: console

    tar -xzvf puppet_ca_backup.tar.gz -C /
    tar -xzvf puppet_ssl_backup.tar.gz -C /

You will then make sure that the user and group permissions are `puppet`. This should already be `puppet`, but it doesn't hurt to double check.

.. code-block:: console

    chown -R puppet:puppet /etc/puppetlabs/puppet/ssl
    chown -R puppet:puppet /etc/puppetlabs/puppetserver/ca

Step 3: Star the Puppet Server
#####################################

.. code-block:: console

    systemctl start puppetserver