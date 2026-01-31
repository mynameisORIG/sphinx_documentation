ldap settings
*******************

Setup
###############

Server
+++++++++++++++++

You first enter your ldap url followed by the port

.. code-block:: console

    ldap://ldap.example.com
    389

Enter the binding user with the binding user password

.. code-block:: console

    cn=admin,dc=example,dc=com

Enter the domain
.. code-block:: console

    cn=dc=example,dc=com

Users
+++++++++++++

Only these object classes: 

.. code-block:: console

    inetOrgPerson
    posixAccount

OCC
###########

Shows current ldap config

.. code-block:: console

    sudo -u apache php ../occ ldap:show-config

Checks if connection works

.. code-block:: console

    sudo -u apache php ../occ ldap:test-config s01

