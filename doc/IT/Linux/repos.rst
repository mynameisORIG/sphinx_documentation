Repo stuff
*******************

Remi
###########

`Remi Blog <https://blog.remirepo.net/post/2021/11/08/Enterprise-Linux-9-Repository>`_

This is for CENTOS or RHEL 9. It provides newer versions of software packages, particularly the PHP stack, for rpm distributions.

.. code-block:: console

    dnf install https://rpms.remirepo.net/enterprise/remi-release-9.rpm
    dnf config-manager --set-enabled remi
    dnf module install php:remi-8.1
    dnf install php80
    module load php80

Oracle Instant Client
###########################

`Oracle Instant Client Download page <https://www.oracle.com/database/technologies/instant-client/linux-x86-64-downloads.html>`_