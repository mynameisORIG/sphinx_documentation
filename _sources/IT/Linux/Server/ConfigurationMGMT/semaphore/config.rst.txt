Semaphore config.json
*************************

url: https://docs.semaphoreui.com/administration-guide/configuration

LDAP
#########################

AD
++++++++++++++++++++++

.. code-block:: console

    "ldap_enable": true,
    "ldap_server": "AD-Users-Computers.hogwarts.edu:636",
    "ldap_needtls": true,
    "ldap_binddn": "CN=user,OU=Accounts,OU=.Users,DC=hogwarts,DC=edu",
    "ldap_bindpassword": "password",
    "ldap_searchdn": "OU=.Users,DC=hogwarts,DC=edu",
    "ldap_searchfilter": "(sAMAccountName=%s)",
    "ldap_mappings": {
            "dn": "distinguishedName",
            "mail": "mail",
            "uid": "sAMAccountName",
            "cn": "cn"
    }

LDAP
++++++++++++++++++++


.. code-block:: console

    "ldap_binddn": "cn=admin,dc=deathstar,dc=com",
    "ldap_bindpassword": "password",
    "ldap_server": "ldap.deathstar.com:389",
    "ldap_searchdn": "ou=People,dc=deathstar,dc=com",
    "ldap_searchfilter": "(&(uid=%s)(memberOf=cn=semaphore,ou=Group,dc=deathstar,dc=com))",
    "ldap_mappings": {
            "dn": "",
            "mail": "uid",
            "uid": "uid",
            "cn": "cn"
    },
    "ldap_enable": true,
    "ldap_needtls": false


Port
#########

.. code-block:: console

    "port": "443"

SSL/TLS
#################

.. code-block:: console

    "tls": {
        "enabled": true,
        "cert_file": "/etc/pki/ca-trust/source/anchors/semaphore.crt",
        "key_file": "/etc/pki/ca-trust/source/anchors/semaphore.key"
    }