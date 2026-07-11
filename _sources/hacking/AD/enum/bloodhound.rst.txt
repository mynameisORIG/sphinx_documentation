Using Bloodhound and Bloodhound-python
*****************************************

Create json files to enumerate stuff with bloodhound

.. code-block:: console

   sudo  bloodhound-python -c ALL -u <username_of_found_user> -p <password_of_found_user> -d <domainName.local> -dc <dc.name.local> -ns ip.of.domain

output

.. code-block:: console

   #######_computers.json
   ######_domains.json
   #######_groups.json
   ##########users.json

start neo4j server

.. code-block:: console

   neo4j console

start bloodhound

.. code-block:: console

   bloodhound

