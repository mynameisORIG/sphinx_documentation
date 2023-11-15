How to see smb files Linux
*******************************

SMBMAP
#########

This will display every file share available on smb

.. code-block:: console

        smbmap -u <userame> -p <password> -H monteverde.htb -R 

example

.. code-block:: console

                .\users$\* 

                        dr--r--r--                0 Fri Jan  3 08:12:48 2020    . 

                        dr--r--r--                0 Fri Jan  3 08:12:48 2020    .. 

                        dr--r--r--                0 Fri Jan  3 08:15:23 2020    dgalanos 

                        dr--r--r--                0 Fri Jan  3 08:41:18 2020    mhope 

                         dr--r--r--                0 Fri Jan  3 08:14:56 2020    roleary 
                
                                dr--r--r--                0 Fri Jan  3 08:14:28 2020    smorgan 

                 .\users$\mhope\* 

                        dr--r--r--                0 Fri Jan  3 08:41:18 2020    . 
                
                        dr--r--r--                0 Fri Jan  3 08:41:18 2020    .. 
                
                        fw--w--w--             1212 Fri Jan  3 09:59:24 2020    azure.xml 

SMBclient
###########

Login using smb

.. code-block:: console

        smbclient -U <username> //monteverde.htb/users$ <password>i

Display Share Names

.. code-block:: console

        smbclient -NL //<hostname> -R

SMBserver
###########

Setup a smb server

.. code-block:: console

        smbserver.py share .

Mount
########

Mounting a share

.. code-block:: console

   mount -t cifs //<ip>/<share> /mnt -o user=<user or blank>,password=<password or blank>
