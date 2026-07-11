Subprocess libraries
*******************************

Acronyms
################

OS -> Operating System

Introduction
####################

This is suppose to be used to help for notes about subprocess. I'll also be mentioning shlex due to it being very valuable alongside subprocess.

What it does
###################

* This allows you to run OS command through python.

Running basic command examples
##################################

basic
-----------

This is a basic example of it. The first code shows a basic example of it

.. code-block:: console

    import shlex
    import subprocess

    subprocess.run(shlex.split("whoami"))

other variables
----------------------

.. code-block:: console

    subprocess.run("echo Hello, World!", shell=True, capture_output=True, text=True)


What `shell=True` does is execute the code through the shell. This is an optional argument.

What `capture_output=True` does is capture output. It will put the output in stdout and stderr.

What `text=True` does is it will return the stdout and stderr as a string, otherwise as bytes.
