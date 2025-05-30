Startup Setup
************************************

Increase Storage (homelab)
####################################

Summary
-------------

We don't need the **local-lvm** storage. So we are going to remove that.


Instructions
---------------------

#. Login into hypervisor
#. Go to Datacenter -> Storage
#. Click **local-lvm**
#. Click **remove**
#. Click **yes**
#. Click the nodename -> shell
#. Run these 3 commands

.. code-block:: console

    lvremove /dev/pve/data
        y
    lvresize -l +100%FREE /dev/pve/root
    resize2fs /dev/mapper/pve-root

You will now notice more data in local to use.