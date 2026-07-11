Setting up FreeIPA client
*****************************

Uninstall freeipa 
######################

.. code-block:: console

    ipa-client-install --uninstall


Installing freeipa client
###############################

.. code-block:: console


    dnf install freeipa-client sssd -y
    authselect enable-feature with-mkhomedir
    systemctl enable --now oddjobd 
    sudo ipa-client-install --hostname=host.deathstar.com --mkhomedir --server=ipa.deathstar.com --domain=deathstar.com --realm=DEATHSTAR.COM --no-ntp --force-join
        Proceed with fixed values and no DNS discovery? [no]: yes
        Continue to configure the system with these values? [no]: yes
        User authorized to enroll computers: admin
        Password for admin@DEATHSTAR.COM:

lxc container
+++++++++++++++++++

If you have an lxc container you are running this on, you need to add an extra step.

.. code-block:: console

    sudo sed -i '/\[domain\/deathstar.com\]/a krb5_ccache_type = FILE' /etc/sssd/sssd.conf

If you don't you get this error **krb5_cc_cache_match failed: [-1750600185][Invalid UID in persistent keyring name]**
