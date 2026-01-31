Keys documentation
#########################

https://zakirpcs.medium.com/how-to-add-gitlab-private-repository-into-ansible-semaphore-b6ae8d669e4d

.. code-block:: console

    echo -n 'P@$$w0rd#2024' | jq -sRr @uri
    P%40%24%24w0rd%232024


To make sure you are able to login with your username and password with the key you need to do the following:

1. Login -> Key Store -> NEW Key
2. Enter the following
 1. Type: Login with password
 2. Login: username
 3. Password: the password you use to encode above
