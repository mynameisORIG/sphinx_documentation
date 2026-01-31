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

Execute single module
#############################

.. code-block:: console

   puppet agent -t --tags <module>

Troubleshooting
#############################

expired certificate
++++++++++++++++++++++++++++++

node P1
-----------

Clean old SSL certs on the agent

.. code-block:: console

   systemctl stop puppet
   rm -rf /etc/puppetlabs/puppet/ssl

puppet server
-----------------------

.. code-block:: console

   puppetserver ca clean --certname proxy-east-payroll.int.hogwarts.edu

node P2
-----------

.. code-block:: console

   puppet agent -t


node (extra)
---------------

If you are still getting issues, you may need to update the ca.pem file

.. code-block:: console

   curl -k https://puppet.hogwarts.edu:8140/puppet-ca/v1/certificate/ca --output /etc/puppetlabs/puppet/ssl/certs/ca.pem
   puppet agent -t

