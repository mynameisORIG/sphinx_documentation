.. _backup_link: (https://assets.nagios.com/downloads/ncpa/docs/Installing-NCPA.pdf)

adding a linux NCPA client
**********************************

Setup
#######################

Install package
+++++++++++++++++++++++

.. code-block:: console

    rpm -Uvh https://assets.nagios.com/downloads/ncpa/ncpa-latest.el9.x86_64.rpm

Config
++++++++++++++

.. code-block:: console
    
    vi /usr/local/ncpa/etc/ncpa.cfg
        ip = 0.0.0.0
        port = 5666
        community_string = <hash>
    systemctl restart ncpa_listener
    
Firewall rule
++++++++++++++++++++

nftables
------------------

.. code-block:: console

    nft add rule ip filter INPUT tcp dport 5666 accept


