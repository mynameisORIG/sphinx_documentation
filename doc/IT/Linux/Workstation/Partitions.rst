Partition Documentation
*****************************************

Pre-Req
###############

These steps assume you have expanded your hard drive from a hypervisor or added a new hard drive.
For these examples we will assume the hard drive is `/dev/sdc`

New Hard Drive Partition setup
###################################

Make sure you see the new Hard Drive with the following command below. 

.. code-block:: console

    fdisk -l

.. code-block:: console

    fdisk /dev/sdc
        n
        p
        <accept defaults for partition number and sectors>

Filetype
+++++++++++++++

xfs
---------

.. code-block:: console

    mkfs.xfs /dev/sdc1

**Note** If you are updating a hard drive to add space, move to updating partition setup **note**

Updating Partition setup
###################################

Resize partition
+++++++++++++++++++++++++

.. code-block:: console

    sudo parted /dev/sdb
    (parted) resizepart 1
    End?  [42.9GB]? 100%
    quit

Notify system of partition changes
+++++++++++++++++++++++++++++++++++++++++++

.. code-block:: console
    echo 1 | sudo tee /sys/class/block/sdb/device/rescan

or
.. code-block:: console
   
    sudo partprobe /dev/sdb

Remount
+++++++++++++

.. code-block:: console

    mount /opt/www

Grow Filesystem
+++++++++++++++++++++

.. code-block:: console

    sudo xfs_growfs /opt/www

verify changes
+++++++++++++++++++++++

    df -h /opt/www