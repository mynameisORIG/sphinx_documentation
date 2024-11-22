.. _backup_link: https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-A15EE2F6-AAF5-40DC-98B7-0DF72E166888.html

[Migrating VM storage]
*****************************

Prereq
##########

* Make sure VM is on

Steps
##########

#.  Right-click the virtual machine and select Migrate.
 #. To locate a virtual machine, select a data center, folder, cluster, resource pool, host, or vApp.
 #. Click the **Virtual Machines** tab.
#. Click **Change storage only** and click **Next**.
#. Select the format for the virtual machine's disks.
#. Select a virtual machine storage policy from the **VM Storage Policy** drop-down menu. \
Storage policies specify storage requirements for applications that run on the virtual machine. \
You can also select the default policy for vSAN or Virtual Volumes datastores. 
#. Select the datastore location where you want to store the virtual machine files. 
#. On the Ready to complete page, review the details and click **Finish**.
