Installing a Universial Forwarder
*******************************************

Main Folders
################

Windows
+++++++++++++

.. code-block:: console

   C:\Program Files\SplunkUniversalForwarder\etc\apps


Linux
++++++++++

.. code-block:: console

   /opt/splunkforwarder/etc/apps

Install
############

Root user
++++++++++++++

.. code-block:: console

    wget -O splunkforwarder-version.x86_64.rpm "https://download.splunk.com/products/universalforwarder/releases/..."
    rpm -ivh splunkforwarder-version.x86_64.rpm


Splunkfwd user
++++++++++++++++++

.. code-block:: console

   su splunkfwd
   /opt/splunkforwarder/bin/splunk start --accept-license
        admin
        admin password
   /opt/splunkforwader/bin/splunk install app /path/to/splunkclouduf.spl

As root user
+++++++++++++++
  
.. code-block:: console

        /opt/splunkforwarder/bin/splunk enable boot-start
        systemctl start SplunkForwarder


Changing UF port
###################

Splunk User
+++++++++++++++++

If you want to change the management port on the Splunk UF

.. codeblock:: console

    cp -rf uncso_all_uf_mgmtport /opt/splunkforwarder/etc/apps/
