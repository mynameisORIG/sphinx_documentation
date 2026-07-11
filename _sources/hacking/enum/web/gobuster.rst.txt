Gobuster web enumeration
****************************

Dir mode - enum web pages
############################

`dir` stands for directory. The `-u` stands for url. The `-w` stands for wordlist. The `-t` stands for number of concurrent threads.

.. code-block:: console

   gobuster dir -u http://<ip>:<optional port> -w <wordlist.txt> -t 50

vhost mode - find vhost subdomains
#####################################

.. code-block:: console

        gobuster vhost -u http://<ip>:<optional port> -w <wordlist> -t 50

       
