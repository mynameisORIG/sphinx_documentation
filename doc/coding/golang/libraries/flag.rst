Flag modules
********************

This module helps with arguments

Lines 1 and 2 below show the flag being an Integer and a String. The var allows this to be defined globally so it can be used in other functions.
Line 3 allows the flags to be parsed from the command line.
Line 4 shows how to access the vmidFlag from the command line

.. code-block:: console

    var vmidFlag = flag.Int("vmid", 0, "Virtual machine ID to run commands on")
    var functionFlag = flag.String("action", "", "Function to execute (e.g., puppet)")
	flag.Parse()
    *vmidFlag

To execute this in the command line, you would do this

.. code-block:: console

    go run main.go -vmid=101 -action=puppet