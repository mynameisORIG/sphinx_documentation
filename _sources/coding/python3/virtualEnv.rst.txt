Virtual Environments
*****************************

What it does
####################

`virtualenv` is a tool to create isolated python environments. You can install python packages without affecting your system python or other projects.
This is essential when

* You wnat to avoid conflicting package versions
* You're working on multiple project swith different dependencies
* You're in a production or testing environment that requires reproducibility

Create a virtual environment
##################################

.. code-block:: console

    python3 -m venv webui

Activate virtual environment
##################################

.. code-block:: console

    cd /opt/Project/webui
    source bin/activate

Exit the virtual environment
###################################

.. code-block:: console

    deactivate


Delete the virtual environment
#########################################

.. code-block:: console

    rm /opt/Project/webui