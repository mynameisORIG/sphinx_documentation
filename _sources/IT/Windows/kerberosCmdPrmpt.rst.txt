Kerberos CMD Prmpt Commands
*****************************

To query which domain controllers were recently contacted by this computer, type:

.. code-block:: console

        klist query_bind

You would find something like this executed

.. code-block:: console

        Current LogonId is 0:0x3e7
        The kerberos KDC binding cache has been queried successfully.

        KDC binding cache entries: (1)

        #0>	RealmName: XOR.COM
                KDC Address: 10.11.1.120
                KDC Name: xor-dc01.xor.com
                Flags: 0 
                DC Flags: 0xe001f3fc -> GC LDAP DS KDC TIMESERV CLOSEST_SITE WRITABLE GTIMESERV FULL_SECRET WS DS_8 PING DNS_DC DNS_DOMAIN DNS_FOREST 
                Cache Flags: 0 


To diagnose a logon session and to locate a logonID for a user or a service, type:

.. code-block:: console

        klist sessions

You would find something like this executed:

.. code-block:: console


        Current LogonId is 0:0x3e7
        [0] Session 0 0:0x5278b XOR-APP59\Administrator NTLM:Interactive
        [1] Session 0 0:0x20451 NT AUTHORITY\ANONYMOUS LOGON NTLM:Network
        [2] Session 1 0:0xeff6 Window Manager\DWM-1 Negotiate:Interactive
        [3] Session 0 0:0x3e4 xor\XOR-APP59$ Negotiate:Service
        [4] Session 0 0:0x682dc XOR-APP59\Administrator NTLM:Interactive
        [5] Session 0 0:0x3e5 NT AUTHORITY\LOCAL SERVICE Negotiate:Service
        [6] Session 1 0:0xf00a Window Manager\DWM-1 Negotiate:Interactive
        [7] Session 0 0:0x8048 \ NTLM:(0)
        [8] Session 0 0:0x3e7 xor\XOR-APP59$ Negotiate:(0)

