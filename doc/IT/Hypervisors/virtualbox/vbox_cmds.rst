vboxmanage cmds
*******************

list running vms
-------------------

.. code-block:: console

   vboxmanage list runningvms

Output should look something like this: "vm-name" {uuid}

`fetch mac <https://superuser.com/questions/634195/how-to-get-ip-address-assigned-to-vm-running-in-background>`_
--------------------------------------------------------------------------------------------------------------------

.. code-block:: console
        
   vboxmanage showvminfo --details vm-uuid | grep MAC

Output should show MAC: <mac_address>


