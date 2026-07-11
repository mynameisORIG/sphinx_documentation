Info about ldapsearch
************************

Find the domain
#################

Find the domain of the machine. '-x' is simple auth, '-s base' sets the scope to base, and 'namingcontexts' returns naming contexts
   
.. code-block:: console

        ldapsearch -x -h <RHOST> -s base namingcontexts

Dump User Data
################

.. code-block:: console

   ldapsearch -h <domain_ip> -x -b "DC=cascade,DC=local" '(objectClass=person)' > <file>
