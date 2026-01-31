firewalld
*****************

List all active zones
##########################

.. code-block:: console

    sudo firewall-cmd --get-active-zones

Show rules for a specific zones
#########################################

.. code-block:: console

    sudo firewall-cmd --zone=public --list-all

List open ports
####################

.. code-block:: console

    sudo firewall-cmd --list-ports
