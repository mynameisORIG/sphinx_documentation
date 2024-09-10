Using Hashcat
****************

colabcat
https://colab.research.google.com/drive/1ZirdC5VIn7yE83lxifarfwbFNvIOgyz8?authuser=4

Cracking a Kerberos hash
##########################

`Go here to see where you get the output_file from <file:///usr/sysadmin/documentation/html/hacking/enum/AD/GetNPUsers.html>`_ .

Cracking a kerberos hash

.. code-block:: console

        hashcat -m 18200 <output_file> /usr/share/wordlists/rockyou.txt --force

Craking a kerberos hash with TGS

.. code-block:: console

        hashcat -m 13100 <output_file> /usr/share/wordlists/rockyou.txt --force

Cracking a SHA2-256 hash
##########################

.. code-block:: console

   hashcat -m 1400 -a 0 <hash> /usr/share/wordlists/rockyou.txt --force

Cracking a Drupal7 hash
##########################

.. code-block:: console

   hashcat -m 7900 <output_file> /usr/share/wordlist/rockyou.txt --force

Cracking FTP, HTTP, SMTP, LDAP Server hash
##############################################

.. code-block:: console

   hashcat -m 1600 <output_file_like_.htpasswd> /usr/share/seclists/Passwords/xato-net-10-million-passwords-100000.txt --user

Cracking PKZIP (Compressed Multi-File)
###############################################

Make sure you turn it into a hash

.. code-block:: console

   hashcat -m 17220 backup.zip.hash /usr/share/wordlists/rockyou.txt --user --force

NTLM
#######

.. code-block:: console

   hashcat -m 1000 hashes4.txt rockyou.txt -O
