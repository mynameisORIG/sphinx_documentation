Install puppet
*********************

Inital setup
###############

packages
+++++++++++++++

.. code-block:: console

   dnf -y install https://yum.puppet.com/puppet-release-el-9.noarch.rpm
   dnf -y install puppetserver

/etc/puppetlabs/puppet/puppet.conf
++++++++++++++++++++++++++++++++++++++

Add the following code to the top of */etc/puppetlabs/puppet/puppet.conf*

.. code-block:: console

        [main]
        server = <puppet server>
        certname = <puppet server>

Restart puppetserver service

.. code-block:: console

   systemctl enable puppetserver; systemctl start puppetserver

Adding a host
##################

List all certs associated with puppet. The certs are the workstations and servers.

.. code-block:: console

   puppetserver ca list -a


Assign a cert to a workstation or host

.. code-block:: console

   puppetserver ca sign --certname <computer>
