Puppet Workstation 
***********************

Configuration
####################

Install puppet-agent
+++++++++++++++++++++++++++++

EL9

.. code-block:: console

   dnf -y install https://yum.puppet.com/puppet-release-el-9.noarch.rpm
   dnf -y install puppet-agent

/etc/puppetlabs/puppet/puppet.conf
+++++++++++++++++++++++++++++++++++++++

.. code-block:: console

        [main]
        server = <puppet server>
        certname = <client>

        [agent]
        server = <puppet server>
        ca_server = <puppet server>
        runinterval = 30m

After making sure everything is in this listed above, restart *puppet* on the client

.. code-block:: console

   systemctl enable --now puppet; systemctl start puppet
