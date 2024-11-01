Requests library
*********************

Introduction
####################

This is suppose to be used to help for notes about the requests library.

What it does
####################

The `requests` library is used to make simple http requests in a simply way.

How to use it
##################

get
+++++++++

The example below shows how to download something using the `get` method.

The `verify=False`, is so you don't have to verify the SSL certs for https.

.. code-block:: console

    import requests

    response = requests.get('https://someRandom.url.com', verify=False)