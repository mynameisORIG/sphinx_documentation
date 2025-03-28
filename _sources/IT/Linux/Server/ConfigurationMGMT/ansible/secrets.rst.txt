Ansible secrets
*************************

url: https://www.redhat.com/en/blog/ansible-playbooks-secrets

setup file encryption
#########################

vault creation
++++++++++++++++++++++

.. code-block:: console

    vi vault.yml
        api_key: SuperSecretPassword
    ansible-vault encrypt vault.yml
        New Vault Pasword
        Confirm new vault password

using in file
++++++++++++++++++++

This below assumes the file is called `main.yml`.

.. code-block:: console

    - name: Ensure API key is present in config file
      ansible.builtin.lineinfile:
        path: /etc/app/configuration.ini
        line: "API_KEY={{ api_key }}"

Running the file
+++++++++++++++++++++++

This below assumes the file is called `main.yml`.

.. code-block:: console

    ansible-playbook -i inventory.ini -e @vault.yml --ask-vault-pass main.yml
