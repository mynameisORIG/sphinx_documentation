How to download files via CLI
*******************************

Windows
#########

Certutil will download files from the internet

.. code-block:: console

        certutil.exe -urlcache -split -f http://webserver/file.you.want C:\location\you\want\to\save\file.you.want

Powershell
++++++++++++++++

.. code-block:: console

	powershell.exe Invoke-WebRequest  http://webserver/file.exe -outfile  file.exe

Linux
#######

Curl will download files from the internet

.. code-block:: console

        curl http://webserver/file.you.want -o name.of.file.you.want
