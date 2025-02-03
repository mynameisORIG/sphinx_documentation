TTY Shells
*************

Python
###########

.. code-block:: console

   python -c 'import pty; pty.spawn("/bin/sh")'

.. code-block:: console

        echo os.system('/bin/bash')

Bash
######

.. code-block:: console

        /bin/sh -i

Perl
######

.. code-block:: console

        perl —e 'exec "/bin/sh";'

Ruby
#######

.. code-block:: console        

         exec "/bin/sh"

Lua
######

.. code-block:: console

   os.execute('/bin/sh')

Within nmap
##############

.. code-block:: console

   !sh
