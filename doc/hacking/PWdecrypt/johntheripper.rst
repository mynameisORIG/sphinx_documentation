John The Ripper PW decyption
*******************************

Rar files
############

The following below will dump the hash contents to a file 

.. code-block:: console 

        rar2john RAR_file.rar > dumpedHASHfile

Then you start John to crack it.

.. code-block:: console 

        john dumpedHASHfile --wordlist=wordlist.txt

Zip files
#############

Create a hash for the zip file

.. code-block:: console

   zip2john file.zip > file.zip.hash

Decrypt with hashcat. You can find the decryption through the hashcat page.

Wordpress (MD5)
#####################

Example hash

.. code-block:: console

        $P$984478476IagS59wHZvyQMArzfx58u. 

CMD

.. code-block:: console

        john --wordlist=/usr/share/wordlists/rockyou.txt hash_file_with_hash_inside
