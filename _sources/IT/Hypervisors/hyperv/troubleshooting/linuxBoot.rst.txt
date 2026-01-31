Linux boot issues 
*******************

SCSI Disk (0,0): The signed image's hash is not allowed (DB) fix
#########################################################################

#. Open Hyper-V Manager.
#. Select the VM showing the error.
#. Right-click the VM and select Settings.
#. In the Settings window, navigate to Security.
#. Uncheck "Enable Secure Boot" and click OK.
#. Reboot the VM to see if it boots properly.