Dashboard troubleshooting
*****************************

API Error: 2001 - Unexpected end of JSON input 
####################################################

This can happen if the memory is full on the server.

The fix

.. code-block:: console

    systemctl stop wazuh-dashboard
    rm  /usr/share/wazuh-dashboard/data/wazuh/config/wazuh-registry.json
    systemctl start wazuh-dashboard

You may need to delete your browser's cache. After naviagte to the wazuh dashboard.