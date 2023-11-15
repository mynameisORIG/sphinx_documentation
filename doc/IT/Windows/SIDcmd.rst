`Find a User's SID in Windows <https://www.lifewire.com/how-to-find-a-users-security-identifier-sid-in-windows-2625149>`_
******************************************************************************************************************************

Find a User's SID with WMIC
#################################

All Users
+++++++++++++

Open up a command prompt and type the following:

.. code-block:: console

   wmic useracount get name,sid

Single User
++++++++++++++

.. code-block:: console

   wmic useraccount where name="USER" get sid

Finding a Username Using the SID
###################################

.. code-block:: console

   wmic useraccount where sid="S-I-D-Number" get name

Find a User;s SID in the REGISTRY
###################################

Go into this registry path `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList` and look for ProfileImagePath


