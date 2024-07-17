SplunkCloud documentation
******************************

Apps
#########

Search and Reporting
+++++++++++++++++++++++

Search queries
-------------------

.. code-block:: console

        index="_internal"
        index="linux"
        index="win"
        index IN ("netfw","netids")
        index="_internal" sourctype=splunkd host=* component=DC* host="hostname"
        index=apache status=!200 | timechart spu=1h count by status
        index="_internal" host!=splunkcloud* log_level!=INFO sourcetype=splunkd componet=ExecProcessor | stats count by host | where count > 1000

