Universal Forwarder troubleshooting
**********************************************

Reset forwarder server
##############################

IP address should be the IP of the Deployment server or IF or HF

.. code-block:: console

    /opt/splunkforwarder/bin/splunk remove forward-server 192.168.1.5:9997
    /opt/splunkforwarder/bin/splunk add forward-server 192.168.1.5:9997 -auth admin:YOUR_PASSWORD_HERE

Check if UF is listening to indexer
++++++++++++++++++++++++++++++++++++++++++

.. code-block:: console

    /opt/splunkforwarder/bin/splunk list forward-server

Check what's being monitored
#######################################

.. code-block:: console

    sudo /opt/splunkforwarder/bin/splunk list monitor

Force a test message
################################

.. code-block:: console

    sudo /opt/splunkforwarder/bin/splunk add oneshot /var/log/messages -sourcetype test:messages -index web