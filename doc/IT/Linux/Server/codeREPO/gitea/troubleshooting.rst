Gitea troubleshooting
******************************

host is not allowed to connect to this mysql server
#######################################################

To do this, please make sure to login to the sql server

Check account access
+++++++++++++++++++++++++++++

.. code-block:: console
    
    SELECT host FROM mysql.user WHERE User = 'root';

IP address add
+++++++++++++++++++++++

This next step adds the IP address of each system that you want to grant access to

.. code-block:: console

    CREATE USER 'root'@'X.X.X.X' IDENTIFIED BY 'RandomPassword';
    GRANT ALL PRIVILEGES ON *.* TO 'root'@'X.X.X.X';

Refresh privileges
+++++++++++++++++++++++++++

.. code-block:: console

    FLUSH PRIVILEGES;

Sources
+++++++++++++++++++++++++++

`stackoverflow <https://stackoverflow.com/questions/19101243/error-1130-hy000-host-is-not-allowed-to-connect-to-this-mysql-server>`_