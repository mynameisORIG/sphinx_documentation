Squid Configuration file
*****************************

This file is hosted in ruby

Networking
#############

Internal Networks
+++++++++++++++++++++

This line allows what networks would be allowed in your proxy

.. code-block:: console

   acl localnet src x.x.x./16

This line tells squid to allow a network and sites. In this example assume *localnet* is the network and *otherguys* is the proxy web ACL. You can also seperate it indiviudally.

.. code-block:: console

   http_access allow localnet otherguys

Ports
++++++++

This controls what port(s) squid is listening too

.. code-block:: console

   http_port 3128
   http_port 80

Sites
#######

This controls what sites you are allowed to view by domain or IP address. This example assumes you already created a folder called *approved-sites* and a file called *safe-sites*.

Consider *otherguys* like a variable. In this file it can be referenced.

.. code-block:: console

   acl otherguys dstdomain "/etc/squid/approved-sites/safe-sites"

Misc configuration
#####################

Logs
++++++++

To control where the access logs go put in the following

.. code-block:: console

   access_log /var/log/squid/access.log

email manager
++++++++++++++++

To put the squid manager's email on squid, put the following into the file

.. code-block:: console

   cache_mgr email@domain.com
