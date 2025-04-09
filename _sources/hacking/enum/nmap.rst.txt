NMAP cheatsheat
*****************

TCP scan all ports
#####################

.. code-block:: console

	nmap -sC -sV -p- <IP>

UDP scan all ports
######################

.. code-block:: console

	nmap -sU -sV -p- <IP>

smb enumeration
####################

.. code-block:: console

	nmap --script smb-vuln* -p 137,139,445 <IP>  

MSSQL enumeration
###################

.. code-block:: console

        nmap --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell,ms-sql-config,ms-sql-ntlm-info,ms-sql-tables,ms-sql-hasdbaccess,ms-sql-dac,ms-sql-dump-hashes --script-args mssql.instance-port=1433,mssql.username=sa,mssql.password=,mssql.instance-name=MSSQLSERVER -sV -p 1433 <IP>        

