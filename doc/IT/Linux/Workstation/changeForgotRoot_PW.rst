Change forgotten root password
***********************************************************************************

Boot Menu
#################

* Select a non-rescue kernel and press `e` on the keyboard
* Search for the text `quiet` and at the end of that line add the following

.. code-block:: console

	rw init=/bin/bash
	
* press `ctrl+x` on the keyboard

shell
###############

mounting
++++++++++++++++

Mount the root partition

.. code-block:: console

	mount -o remount,rw /
	
changing the root password
+++++++++++++++++++++++++++++++++

Type this command to change the root password

.. code-block:: console

	passwd root
	
finishing up
+++++++++++++++++

.. code-block:: console

	touch /.autorelabel
	exec /sbin/init