Selinux stuff
******************

setroubleshootd service goes into failed state if SELinux is disabled
#############################################################################

web: https://access.redhat.com/solutions/7003350

solution
++++++++++++++++

.. code-block:: console

    mkdir -p /etc/systemd/system/setroubleshootd.service.d
    cat > /etc/systemd/system/setroubleshootd.service.d/selinux.conf << EOF
    [Unit]
    ConditionSecurity=selinux
    EOF
    systemctl daemon-reload
    systemctl reset-failed setroubleshootd.service
