Setup LDAP or AD Authentication
***************************************

This is so whenever you sign into proxmox ve, you can login through your ldap account.

You will first need to go to the following:

#. Click into Datacenter -> Permissions -> Realms
#. Click Add 
  #. Click LDAP Server or Active Directory Server

LDAP
#############

Enter the following for each section similarly with the output below in the General Section:

.. code-block:: console

    Base Domain Name: dc=hogwarts,dc=com
    User Attribute Name: uid
    Server: X.X.X.X
    Mode: Default (LDAP)

Enter the following for each section similarly with the output below in the Sync Option Section:

.. code-block:: console

    Bind User: cn=admin,dc=hogwarts,dc=com
    Bind Password: <password>
    User classes: person
    Group classes: posixGroup
    Groupname attr: cn

Make sure you hit ok.

AD
########

Fill this out when you have done this with an AD Server

Sync
##########

You then click the new realm, and select sync. You have two options of **preview** and **sync**. Choose one and then you should be able to login.