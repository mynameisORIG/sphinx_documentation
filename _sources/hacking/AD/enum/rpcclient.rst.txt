rpclient cmds
*******************

Go into rpcclient
###################

.. code-block:: console

   sudo rpcclient -U <domain>\\<user> <domain_ip>
   sudo rpcclient -U "" -N <LHOST>

Get Domain Users
###################

.. code-block:: console

   rpcclient $> enumdomusers
   rpcclient $> enumdomusers > <users.txt>
   cat <users.txt> | cut -d "[" -f 2 | cut-d "]" -f 1

Get more information about Domain User
#########################################

.. code-block:: console

   queryuser <user_rid>
   
Get Domain Groups
####################

.. code-block:: console

   enumdomgroups

Get More Info about Group
#############################

.. code-block:: console

   querygroup <group_rid>

Get Group Member Information
###############################

.. code-block:: console

   querygroupmem <group_rid>

Enumerate All Privileges
#############################

.. code-block:: console

   enumprivs

Enumerate Printers
#####################

.. code-block:: console

        enumprinters
