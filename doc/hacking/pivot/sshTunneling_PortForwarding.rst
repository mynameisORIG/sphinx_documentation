SSH Tunnelling / Port Forwarding 
************************************

SSH
#######

Forward Connections
+++++++++++++++++++++++

There are two ways to create a forward SSH tunnel using the SSH client -- port forwarding, and creating a proxy.

* Port forwarding is accomplished with the -L switch, which creates a link to a Local port. For example, if we had SSH access to 172.16.0.5 and there's a webserver running on 172.16.0.10, we could use this command to create a link to the server on 172.16.0.10:

.. code-block:: console

    ssh -L 8000:172.16.0.10:80 user@172.16.0.5 -fN

* Proxies are made using the -D switch, for example: -D 1337. This will open up port 1337 on your attacking box as a proxy to send data through into the protected network. This is useful when combined with a tool such as proxychains. An example of this command would be:

.. code-block:: console
  
   ssh -D 1337 user@172.16.0.5 -fN  

Reverse Connections
+++++++++++++++++++++++++++

Look up

sshuttle
##############

.. code-block:: console
        
        sshuttle -r user@address --ssh-cmd "ssh -i KEYFILE" SUBNET -x <IP>
        sshuttle -r linux-admin@admin.holo.live --ssh-cmd "ssh -i /home/yekki/.ssh/id_rsa" 10.200.142.0/24 -x 10.200.142.33

