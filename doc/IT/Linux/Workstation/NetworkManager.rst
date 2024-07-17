Network NetworkManager
***************************

Show connection settings
#############################

.. code-block:: console
    
    nmcli dev show

Show different connections
##############################

.. code-block:: console

    nmcil con show

Modify connection
###################

* ipv4.gateway <X.X.X.X>
* ipv4.dns "X.X.X.1 X.X.X.2"

.. code-block:: console

    nmcli con mod eth0 <from the above list>

Turn NetworkManager on and off
##################################

.. code-block:: console