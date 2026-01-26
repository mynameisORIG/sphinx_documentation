ldap settings
*******************

update
###############

Make sure to do a hypervisor backup of the vm or container if you do `no-backup`

.. code-block:: console

    sudo -u apache php occ maintenance:mode --on
    sudo -u www-data php /path/to/nextcloud/updater/updater.phar --no-backup
        y
        y
        N
    dnf update -y
    reboot


