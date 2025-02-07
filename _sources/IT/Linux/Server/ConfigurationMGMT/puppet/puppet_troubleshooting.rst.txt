Troubleshooting puppet
*****************************

The certificate for 'CN=XXXX' does not match its private key
##################################################################

Client
+++++++++

Remove the SSL folder and stop puppet

.. code-block:: console
	
	cd  /etc/puppetlabs/puppet/ssl
	rm ./*
	systemctl stop puppet
	
Server
++++++++++++++

Find the cert and remove it.

.. code-block:: console

	puppetserver ca list -a | less
	puppet node clean HOST
	puppet node clean sftp-east.unc.cloud
	
Client
++++++++++++++

run puppet and turn on puppet

.. code-block:: console

	puppet agent -t
	systemctl start puppet