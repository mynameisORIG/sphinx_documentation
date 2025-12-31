Commands you can run on the indexer
********************************************

Delete dispatch directory data
######################################

.. code-block:: console

    sudo -u splunk /opt/splunk/bin/splunk clean eventdata -f dispatch

This command deletes all search job artifacts stored in Splunk’s dispatch directory.

Location of dispatch directory

.. code-block:: console

    /opt/splunk/var/run/splunk/dispatch/

It contains temporary folders created whenever a search runs — including:

* Search results
* Search metadata
* CSV/JSON result sets
* Summary artifacts
* Pivot artifacts
* Lookup artifacts
* Scheduled search result bundles

Running the command:
---------------------------

* Removes all completed search job artifacts
* Removes stale or expired dispatch folders
* Does NOT remove indexed data
* Can break currently running searches

What it doesn't do
-----------------------

* It does not delete indexes
* It does not delete events
* It does not delete Splunk configs
* It does not delete saved searches
* It does not delete dashboards or knowledge objects

When you should run it
-------------------------------

* The minimum free disk space (5000MB) reached for /opt/splunk/var/run/splunk/dispatch.
* Search process did not exit cleanly
* job expired but dispatch directory still exists
