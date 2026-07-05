troubleshooting
********************

/var/ossec/queue/vd/feed has a tone of data being used
##################################################################

.. code-block:: console

    cd /var/ossec/queue/vd/feed
    systemctl stop wazuh-manager
    rm -rf /var/ossec/queue/vd/feed/*
    systemctl start wazuh-manager

wazuh-indexer service issues
##################################

Caused by: java.net.BindException: Cannot assign requested address
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

You need to change the network host of the indexer.

.. code-block:: console

    vi /etc/wazuh-indexer/opensearch.yml
        network.host: 192.168.1.103
    systemctl restart wazuh-indexer