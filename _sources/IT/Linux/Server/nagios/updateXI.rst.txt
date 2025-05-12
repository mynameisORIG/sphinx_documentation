.. _backup_link: https://assets.nagios.com/downloads/nagiosxi/docs/XI-Upgrade-Instructions.pdf

[Updating Nagios XI]
****************************

.. code-block:: console

    cd /tmp
    rm -rf nagiosxi xi*.tar.gz
    wget http://assets.nagios.com/downloads/nagiosxi/xi-latest.tar.gz
    tar xzf xi-latest.tar.gz
    cd nagiosxi
    ./upgrade

You can choose what version here: https://assets.nagios.com/downloads/nagiosxi/versions.php