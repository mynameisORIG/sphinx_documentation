nftables
*******************************

Sources
##############

`ibm <https://www.ibm.com/docs/en/storage-scale/5.1.9?topic=gui-migrating-iptables-rules-nftables>`_

Migrating iptables rules to nftables
########################################

Iptables backup
++++++++++++++++++++++++

Create a backup of the iptables rules

.. code-block:: console

    iptables-save | tee /tmp/iptables.dump

Convert iptables to nftables
++++++++++++++++++++++++++++++++++++

.. code-block:: console

    iptables-restore-translate -f /tmp/iptables.dump | tee /tmp/nftables/ruleset.nft

Implement nftables rules
++++++++++++++++++++++++++++++++

.. code-block:: console

    nft --check -f ./file
    nft -f ./file

Verify ruleset
++++++++++++++++++++++

.. code-block:: console

    nft list ruleset