Using Kerbrute
*****************

Finding users
################

You will first need to run the `ldapsearch <file:///usr/sysadmin/documentation/html/hacking/enum/AD/ldapsearch.html>`_ command to find the domain name. Once you do, you can then run this command.

.. code-block:: console

   /home/git/kerbrute/kerbrute_linux_amd64 userenum -d <domain.name> <username.txt file> --dc <DOMAIN_RHOST> 


