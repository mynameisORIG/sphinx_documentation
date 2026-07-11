talk occ cli
*****************

bots
###################

install
+++++++++++++

.. code-block:: console

    php occ talk:bot:install <bot name> <secret_key_48_to_128_characters> "https://<nextcloud URL>/ocs/v2.php/apps/spreed/api/v1/chat/<chatroom id>" "Wazuh alerts bot"

uninstall
+++++++++++++++

.. code-block:: console

    php occ talk:bot:uninstall <id>

list
++++++++

.. code-block:: console

    php occ talk:bot:list

test a bot
+++++++++++++++++

.. code-block:: console

    curl -k -u <bot_name>:<secret_key> "https://<nextcloud URL>/ocs/v2.php/apps/spreed/api/v1/chat/fenbj7m4"   -H 'accept: application/json, text/plain, */*'   -H 'cache-control: no-cache'   -H 'content-type: application/json'   -H "OCS-APIRequest: true"   --data-raw '{"message":"test123"}'

talk
############

Create a talk room
++++++++++++++++++++++

.. code-block:: console

    php occ talk:room:create "Wazuh Alerts"