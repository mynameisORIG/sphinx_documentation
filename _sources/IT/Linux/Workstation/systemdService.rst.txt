systemdService
******************************************************

Create a systemd service
###############################

go to this folder location

.. code-block:: console

    cd /etc/systemd/system/serviceNAME.service

This is what basic homemade service should look like

.. code-block:: console

    [Unit]
    Description=ROT13 demo service
    After=network.target
    StartLimitIntervalSec=0
    
    [Service]
    Type=simple
    Restart=always
    RestartSec=1
    WorkingDirectory=/opt/homepage
    ExecStart=/usr/bin/env php /path/to/server.php

    [Install]
    WantedBy=multi-user.target