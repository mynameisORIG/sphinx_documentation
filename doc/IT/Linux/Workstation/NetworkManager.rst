Network NetworkManager
***************************

Commands
############

Show connection settings
==================================

.. code-block:: console
    
    nmcli dev show

Show different connections
===================================

.. code-block:: console

    nmcli con show

Modify connection
======================================

* ipv4.gateway <X.X.X.X>
* ipv4.dns "X.X.X.1 X.X.X.2"

.. code-block:: console

    nmcli con mod eth0 <from the above list>

Turn off IPv6
====================================

.. code-block:: console

    nmcli con mod eth0 ipv6.method "disabled"
    nmcli con up eth0

Turn NetworkManager on and off
========================================

.. code-block:: console

    nmcli con up "eth0"
    nmcli con down "eth0"

Create a bond
================================

active-backup
=========================

Active-backup ensures only one interface is active at a time for redundancy

.. code-block:: console

    sudo nmcli connection add type bond con-name bond0 ifname bond0 mode active-backup
    sudo nmcli connection add type ethernet con-name bond0-slave-wlp1s0 ifname wlp1s0 master bond0 primary wlp1s0
    sudo nmcli connection add type ethernet con-name bond0-slave-eno2 ifname eno2 master bond0 primary wlp1s0

    nmcli con up bond0
    ip add sh bond0

Files
###############

The location for the network file should be around here:

.. code-block:: console

    cd /etc/NetworkManager/system-connections

The file should look something like This

.. code-block:: console

    vi ens192.nmconnection

ipv4 section
========================

The following shows how to input an ipv4 address, it's gateway, it's dns, and the method it uses to get this.

There are different methods: **auto** and **manual**

.. code-block:: console

    [ipv4]
    address1=192.168.1.1/25
    gateway=192.168.1.254
    dns=192.168.1.17
    method=manual

