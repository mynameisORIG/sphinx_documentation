How to uninstall morpheus agents
*****************************************

Source: https://docs.morpheusdata.com/en/6.0.4/troubleshooting/Morpheus_Agent.html#linux-agents

Linux
##########

.. code-block:: console

    sudo yum -y remove morpheus-node morpheus-vm-node
    sudo yum clean all
    sudo systemctl stop morpheus-node-runsvdir
    sudo rm -f /etc/systemd/system/morpheus-node-runsvdir.service
    sudo systemctl daemon-reload
    sudo rm -rf /var/run/morpheus-node /opt/morpheus-node /etc/morpheus /var/log/morpheus-node
    sudo pkill runsv 
    sudo pkill runsvdir
    sudo pkill morphd
    sudo usermod -l morpheus-old morpheus-node

Windows
################

.. code-block:: console

    $app = Get-WmiObject -Class Win32_Product -Filter "Name = 'Morpheus Windows Agent'"
    $app.Uninstall()