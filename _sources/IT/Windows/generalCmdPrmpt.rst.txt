Command Prompt CMDS
**********************

See local users

.. code-block:: console

   net user

See Active Directory users

.. code-block:: console

   net user /domain

Find more information about Active Directory user

.. code-block:: console

   net user <username> /domain

Find groups in domain

.. code-block:: console

   net group /domain

Create a new admin user with admin and remote desktop permissions

.. code-block:: console

   net user /add mynameis password123
   net localgroup administrators mynameis /add
   net localgroup remotedeskupusers mynameis /add
