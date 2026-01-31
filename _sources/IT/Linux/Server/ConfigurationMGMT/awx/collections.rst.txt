collections documentation
*********************************

Collections are kind of like modules or libraries in different programming languages.

The structure should look like this

.. code-block:: console

    project-root/
    ├── collections/
    │   └── requirements.yml
    ├── playbooks/
    │   └── rhel8-patch-cycle.yml
    ├── inventory/
    │   └── hosts
    ├── roles/
    └── vars/

The requirements.yml file should look like this

.. code-block:: console

    ---
    collections:
    - name: community.general
        version: "10.5.0"