Wordpress enum
****************

Enumerate
######################

To find useful information such as wordpress users and vulnerabilites and version with this command:

.. code-block:: console

   wpscan --url "http://IP/wordpress" --enumerate

Find Wordpress User Password
################################

Bruteforce password to get login credentials

.. code-block:: console

   wpscan --url "http://IP/wordpress -U <user> -P /usr/share/wordlists/rockyou.txt
