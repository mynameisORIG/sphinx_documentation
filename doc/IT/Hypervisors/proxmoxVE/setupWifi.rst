Setting up wifi for Proxmox
*********************************

Pre
#############

Please make sure ethernet cable is still plugged in.

Packages
##############

.. code-block:: console

    apt update
    apt install wireless-tools wpasupplicant

interfaces files
####################

You need to edit the **`/etc/network/interfaces`** file

.. code-block:: console

    auto wlp1s0
    iface wlp1so inet dhcp
        wpa-ssid "YourSSID"
        wpa-psk "WiFiPassword"

Restart Networking
#########################

.. code-block:: console

    systemctl restart networking