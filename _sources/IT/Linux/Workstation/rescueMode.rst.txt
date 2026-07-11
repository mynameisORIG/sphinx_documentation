Rescue Mode
*********************

Dracut-initque timeout does not exist
#########################################

The error would look something like this

.. code-block:: console

    dracut-initque timeout /dev/mapper/rhel-root does not exist
    dracut-initque timeout /dev/rhel/root does not exist
    dracut-initque timeout /dev/rhel/swap does not exist

The fix
++++++++++++++

#. Download the OS iso file
#. Mount the iso file to the VM or machine
#. shut down the machine or VM
#. either change boot settings to have dvd first or select the dvd
#. turn on VM
#. select troubleshooing
#. 1(continue)
#. chroot to the system root
  #. `chroot /mnt/sysimage` -> rhel7
  #. `chroot /mnt/sysroot` -> rhel9
#. rebuild initramfs
  #. `dracut --force`
#. `exit`
#. shutdown vm again
#. change boot back if you edited the boot list
#. start vm
