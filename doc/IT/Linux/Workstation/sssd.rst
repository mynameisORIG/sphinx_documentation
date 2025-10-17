SSSD Service
******************

sssd.conf file
#####################

This file is located in the `/etc/sssd/` directory.

OpenLdap
++++++++++++++++

.. code-block:: console

    [sssd]
    config_file_version = 2
    services = nss, pam, autofs, ssh, sudo
    domains = default

    [nss]
    homedir_substring = /home
    memcache_timeout = 600

    [domain/default]

    id_provider = ldap
    auth_provider = ldap
    chpass_provider = ldap
    ldap_uri = ldap://ldap.deathstar.com/
    ldap_search_base = dc=deathstar,dc=com
    ldap_id_use_start_tls = True
    ldap_tls_cacertdir = /etc/openldap/certs
    cache_credentials = True
    ldap_tls_reqcert = allow


    [nss]
    homedir_substring = /home
    memcache_timeout = 600

Active Directory
++++++++++++++++++++++++++++++

.. code-block:: console

    [sssd]
    domains = ad.hogwarts.edu
    config_file_version = 2
    services = nss, pam

    [domain/ad.hogwarts.edu]
    ad_domain = ad.hogwarts.edu
    krb5_realm = ad.hogwarts.edu
    realmd_tags = manages-system joined-with-adcli
    cache_credentials = True
    id_provider = ad
    krb5_store_password_if_offline = True
    default_shell = /bin/bash
    ldap_id_mapping = True
    use_fully_qualified_names = True
    fallback_homedir = /home/%u@%d
    access_provider = ad
    ad_gpo_ignore_unreadable = True
    ad_access_filter = (|(memberOf=cn=SuperDuper,ou=Linux,dc=ad,dc=hogwarts,dc=edu)(memberOf=cn=Websters,ou=Linux,dc=ad,dc=hogwarts,dc=edu))
    ad_gpo_access_control = disabled


Troubleshooting
##########################

Backend is offline
+++++++++++++++++++++++

If you see `Backend is offline` when running `systemctl status sssd`, you should probably restart the sssd service.

.. code-block:: console

    systemctl restart sssd

Failed to initalize credentials using keytab [MEMORY:/etc/krb5.keytab]: Preautehtnication Failed
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

https://access.redhat.com/solutions/3380341

Use realm list to grab the information to join. You'll want to know the **domain-name** and the **realm-name**

.. code-block:: console

    realm list
    
leave the realm

.. code-block:: console

    realm leave

remove the files

.. code-block:: console

    rm -rf /etc/krb5.keytab
    rm -rf /var/lib/sss/db/*
    rm -rf /var/lib/sss/mc/*
    rm -rf /etc/sssd/sssd.conf

join back again

.. code-block:: console

    realm -v domain-name -U user.name@realm-name