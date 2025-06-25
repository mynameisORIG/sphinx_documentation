Networking for lxc
######################

To reconfigure the lxdbr0 subnet
#########################################

.. code-block:: console

    lxc network set lxdbr0 ipv4.address 192.168.1.1/24
    lxc network set lxdbr0 ipv4.dhcp.ranges 192.168.1.10-192.168.1.250

Reconfigure static IP of Container
#########################################

.. code-block:: console

    lxc config device add testCentos eth0 nic \
        nictype=bridged \
        parent=lxdbr0 \
        ipv4.address=192.168.1.172

        lxc restart <Container>
        lxc exec <Contiainer> -- ip addr

