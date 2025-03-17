Argparse library documentation
*****************************************

Introduction
####################

This is suppose to be used to help for notes about the argparse library.

What it does
####################

The `argparse` library is used to make arguments simple with documentation.

How to use it
##################

importing
+++++++++++++++++++

.. code-block:: console

    import argparse

creating arguments
+++++++++++++++++++++++++

The below assumes this is in the args function. This will return the parser arguments

args function
--------------------

This adds arguments for the script

.. code-block:: console

    parser = argparse.ArgumentParser(description="Get information on AD")
    parser.add_argument("--adminUSER", "-a", type=str, help="admin user used to authetnicate to AD server")
    return parser.parse_args()

main function
--------------------

.. code-block:: console

    args = args()

Execution
-----------------

.. code-block:: console

    test.py --adminUSER jdoe