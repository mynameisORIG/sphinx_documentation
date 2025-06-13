Wazuh scripts
********************

link: https://documentation.wazuh.com/current/user-manual/agent/agent-management/remote-upgrading/upgrading-agent.html

agent_upgrade
######################

updating agent
------------------------

This lists the agents that need to be updated

.. code-block:: console

    /var/ossec/bin/agent_upgrade -l

this updates the agents

.. code-block:: console

    /var/ossec/bin/agent_upgrade -a 003 --package_type rpm
    /var/ossec/bin/agent_upgrade -a 003 --package_type deb


manage agent
#####################


list agents
---------------------

.. code-block:: console

    /var/ossec/bin/manage_agents -l

remove agents
---------------------

.. code-block:: console

    /var/ossec/bin/manage_agents -r <agentID>