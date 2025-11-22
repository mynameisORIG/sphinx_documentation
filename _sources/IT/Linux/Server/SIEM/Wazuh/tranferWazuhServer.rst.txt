Transfering Wazuh Server
**********************************

# https://groups.google.com/g/wazuh/c/ndasy4fBMwE?pli=1

This is documentation on how to transfer wazuh data from one server to another

First make sure the wazuh-dashboard is stopped

.. code-block:: console

    systemctl stop wazuh-dashboard

Then copy the files over to the new server

*  cp -p /var/ossec_backup/etc/client.keys /var/ossec/etc/
*  cp -p /var/ossec_backup/etc/ossec.conf /var/ossec/etc/
*  cp -p /var/ossec_backup/queue/rids/sender_counter /var/ossec/queue/rids/sender_counter

This applies to local changes

* cp -p /var/ossec_backup/etc/local_internal_options.conf /var/ossec/etc/local_internal_options.conf
* cp -p /var/ossec_backup/rules/local_rules.xml /var/ossec/etc/rules/local_rules.xml
* cp -p /var/ossec_backup/etc/local_decoder.xml /var/ossec/etc/decoders/local_decoder.xml

This applies to centralized configurations

*  cp -p /var/ossec_backup/etc/shared/agent.conf /var/ossec/etc/shared/default/agent.conf

optional files to copy over

* cp -rp /var/ossec_backup/logs/archives/* /var/ossec/logs/archives
* cp -rp /var/ossec_backup/logs/alerts/* /var/ossec/logs/alerts
* cp -rp /var/ossec_backup/queue/rootcheck/* /var/ossec/queue/rootcheck
* cp -rp /var/ossec_backup/queue/syscheck/* /var/ossec/queue/syscheck

Start the wazuh-dashboard server

.. code-block:: console

    systemctl start wazuh-dashboard

Make sure the New Wazuh server is pointed to the old Wazuh server