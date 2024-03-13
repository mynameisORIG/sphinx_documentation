Installing a Universial Forwarder
*******************************************

Backup for Deployment Linux
###############################

/opt/splunk/etc


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

Windows Install
++++++++++++++++++++

splunk.msi
Accept License
On-Prem
Leave Deployment Server blank
Leave receiver blank
okay
install

Linux Install
++++++++++++++++++

Root user
---------------

.. code-block:: console

    wget -O splunkforwarder-version.x86_64.rpm "https://download.splunk.com/products/universalforwarder/releases/..."
    rpm -ivh splunkforwarder-version.x86_64.rpm


Splunkfwd user
--------------------

.. code-block:: console

   su splunkfwd
   /opt/splunkforwarder/bin/splunk start --accept-license
        admin
        admin password
The bottom is only for IF

.. code-block:: console

   /opt/splunkforwader/bin/splunk install app /path/to/splunkclouduf.spl
   mv X_if_forwarders_inputs /opt/splunkforwarder/etc/apps/
   mv X_all_deploymentclient_folder /opt/splunkforwarder/etc/apps/
   mv X_all_uf_mgmtport_folder /opt/splunkforwarder/etc/apps/

The bootom is for UF

.. code-block:: console

   mv X_if_forwarders_inputs /opt/splunkforwarder/etc/apps/


As root user
-------------------
  
.. code-block:: console

        mv X_all_deploymentclient_folder /opt/splunkforwarder/etc/apps/
        /opt/splunkforwarder/bin/splunk enable boot-start
        systemctl start SplunkForwarder


Changing UF port
###################

Splunk User
+++++++++++++++++

If you want to change the management port on the Splunk UF

.. codeblock:: console

    cp -rf uncso_all_uf_mgmtport /opt/splunkforwarder/etc/apps/
