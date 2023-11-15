Votalitiy
*****************

ID image info and profiles
################################

This plugin will take the provided memory dump and assign it a list of the best possible OS profiles.

.. code-block:: console

   python3 vol.py -f <file.vmem> windows.info
   python3 vol.py -f <file.vmem> linux.info
   python3 vol.py -f <file.vmem> mac.info

Listing Processes and Connections
########################################

pslist
++++++++++

this plugin will get the list of processes from the doubly-linked list that keeps track of processes in memory, equivalent to the process list in task manager.

.. code-block:: console

    python3 vol.py -f <file.vmem> windows.pslist
    python3 vol.py -f <file.vmem> linux.pslist
    python3 vol.py -f <file.vmem> mac.pslist

psscan
+++++++++++++

this technique of listing processes will locate processes by finding data structures that match `_EPROCESS`. While this technique can help with evasion countermeasures, it can also cause false positives.

.. code-block:: console

    python3 vol.py -f <file.vmem> windows.psscan
    python3 vol.py -f <file.vmem> linux.psscan
    python3 vol.py -f <file.vmem> mac.psscan

pstree
+++++++++++++

this plugin will list all processes based on their parent process ID, using the same methods as `pslist`.

.. code-block:: console

    python3 vol.py -f <file.vmem> windows.pstree
    python3 vol.py -f <file.vmem> linux.pstree
    python3 vol.py -f <file.vmem> mac.pstree

netstat
+++++++++++++++

`netstat` will attempt to identify all memory structures with a network connection.

.. code-block:: console

    python3 vol.py -f <file.vmem> windows.netstat
    python3 vol.py -f <file.vmem> linux.netstat
    python3 vol.py -f <file.vmem> mac.netstat

dlllist
+++++++++++++

This plugin will list all DLLs associated with processes at the time of extraction. This can be especially useful once you have done further analysis and can filter output to a specific DLL that might be an indicator for a specific type of malware you believe to be present on the system.

.. code-block:: console

    python3 vol.py -f <file.vmem> windows.dllist
    python3 vol.py -f <file.vmem> linux.dllist
    python3 vol.py -f <file.vmem> mac.dllist

Advanced Memory Forensics
##########################

ssdt
+++++++++

The `ssdt` plugin will search for hooking and output its results. Hooking can be used by legitimate applications, so it is up to you as the analyst to identify what is evil.

.. code-block:: console

   python3 vol.py -f <file.vmem> windows.ssdt
   python3 vol.py -f <file.vmem> linux.ssdt
   python3 vol.py -f <file.vmem> mac.ssdt

modules
+++++++++

The `modules` plugin will dump a list of loaded kernel modules; this can be useful in identifying active malware. However, if a malicious file is idly waiting or hidden, this plugin may miss it.

.. code-block:: console

   python3 vol.py -f <file.vmem> windows.modules
   python3 vol.py -f <file.vmem> linux.modules
   python3 vol.py -f <file.vmem> mac.modules

driverscan
++++++++++++++++

The `driverscan` plugin will scan for drivers present on the system at the time of extraction. This plugin can help to identify driver files in the kernel that the modules plugin might have missed or were hidden.

.. code-block:: console

   python3 vol.py -f <file.vmem> windows.driverscan
   python3 vol.py -f <file.vmem> linux.driverscan
   python3 vol.py -f <file.vmem> mac.driverscan

other plugins
+++++++++++++++++

* modscan
* driverirp
* callbacks
* idt
* apihooks
* moddump
* handles

