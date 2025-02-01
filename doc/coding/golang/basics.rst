Basic golang code
****************************

Running it
#################

.. code-block:: console

    go run file.go

Variables
##################

Source: https://stackoverflow.com/questions/49826038/how-to-add-variable-to-string-variable-in-golang

This creates a variable called data with the integer data 14. This also shows how to use it in the response variable

.. code-block:: console

    data := 14
    response := fmt.Sprintf("Variable string %d content", data)
    fmt.Println(response)