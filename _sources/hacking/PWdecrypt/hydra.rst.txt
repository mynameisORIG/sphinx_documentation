Hydra PW decyption
*******************************

FTP
############

The following below will try to figure out the Password for user.txt. In user.txt you will find the users you enumerated from wherever, and put it into a list. 

.. code-block:: console 

        hydra -L users.txt -P /wordlist/for/password/cracking.txt <victim_IP> ftp -V -f

Then you start John to crack it.

.. code-block:: console 

        john dumpedHASHfile --wordlist=wordlist.txt
