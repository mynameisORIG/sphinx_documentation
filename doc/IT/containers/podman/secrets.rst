Creating podman secrets
*******************************

This is so you can encrypt passwords in your podman compose.
You'll need to create a file with the password. After you run the podman secret command found below, you'll delete the file with the password in it.


.. code-block:: console
    
    podman secret create semaphore_local_admin_password password.txt

    podman secret create --replace semaphore_local_admin_password password.txt
    podman-compose up -d --force-recreate

    podman secret ls