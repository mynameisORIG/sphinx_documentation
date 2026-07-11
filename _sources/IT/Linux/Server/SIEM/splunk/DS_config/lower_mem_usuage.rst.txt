Steps to lower memory usuage
##################################

/opt/splunk/etc/system/local/limits.conf

.. code-block:: console

    [search]
    max_mem_usage_mb = 512
    min_memory_per_search = 64MB
    enable_memory_tracker = 1

    [search_scheduler]
    max_searches_per_cpu = 1

stops splunk from balloning up into swap

.. code-block:: console

    [search]
    search_process_memory_usage_percentage_threshold = 15

limits how much system RAM a single search process may use. 15 is 15%

.. code-block:: console

	[scheduler]
	max_searches_perc = 25

limits how many scheduled searchs can run concurrently

/opt/splunk/etc/system/local/server.conf

add the following

.. code-block:: console

    [pipelines]
    parallelIngestionPipelines = 1

boosts stability in low-RAM systems

/opt/splunk/etc/system/local/indexing.conf


Disable indexing on DS
########################

/opt/splunk/etc/system/local/server.conf

