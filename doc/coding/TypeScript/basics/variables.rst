variables
*********************

types
#############

This shows what types of variables you can create

string
++++++++++++++

This shows how to create a string variable. In this example we will use **firstPlace** as the variable name. The data it will store is **Hello World**.

.. code-block:: console

    let firstPlace: string = "Hello World";

number
++++++++++++

This shows how to create a number variable. In this example we will use **userID** as the variable name. The data it will store is **123456**.

.. code-block:: console

    let userID: number = 123456

boolean
++++++++++++++++++

This shows how to create a boolean variable. In this example we will use **isLoggedIn** as the variable name. The data can only be **true** or **false**.

.. code-block:: console

    let isLoggedIn: boolean = false

any
+++++++++++++++++++++

**Do not use this! This is bad practice**

This basically allows you to not to worry about the type of variable

.. code-block:: console
    
    let obj: any = "string"


extra
############

.toFixed
+++++++++++++++++

The `.toFixed()` corrects on what the variable should be.

.. code-block:: console

    userID.toFixed()

.toLowerCase
+++++++++++++++++++

This can only be used in a string variable. This will make it all lowercase after you define the string

.. code-block:: console

    firstPlace.toLowerCase()