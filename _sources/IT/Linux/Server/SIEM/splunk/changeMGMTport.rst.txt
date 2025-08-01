Change the MGMT port of the Universial Forwarders
*******************************************************

link: https://community.splunk.com/t5/Getting-Data-In/Change-Splunk-management-port-for-single-Linux-host/m-p/517733

Steps
###########

Pre-Req
------------------

This assumes you have already installed the splunk UF package to the host. This step is right before accepting the splunk license.

File
-------------

The code below assumes you want to change the Managment port to `8900`. The **default management port** is `8089`

.. code-block:: console
 
    su splunkfwd
    vi /opt/splunkforwarder/etc/system/local/web.conf
        [settings]
        mgmtHostPort = 127.0.0.1:8900

You would then proceed to accept the license. Afterwards you can delete this file.
