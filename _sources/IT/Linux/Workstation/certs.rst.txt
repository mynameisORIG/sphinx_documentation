Certification information
********************************

Convert pem into crt file
#################################

Location: https://stackoverflow.com/questions/19979171/how-to-convert-pem-into-key

.. code-block:: console

    openssl x509 -outform der -in you-cert.pem -out your-cert.crt