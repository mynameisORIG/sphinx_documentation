vim
****************

Saving
############

#. Press `ZZ` when out of insert or visualize mode
#. Press `:` and then `wq`

Commenting/uncommenting out multiple lines
#################################################

Commenting
-------------

#. Move the cursor to the beginning of the section you want to comment out
#. Press uppercase V to enter **visual line mode**
#. let go of the v character
#. Use the arrow keys to select the lines
#. press `:`
#. type `s/^/#/`
#. press enter

Uncommenting
-----------------

#. Move the cursor to the beginning of the section you want to comment out
#. Press uppercase V to enter **visual line mode**
#. let go of the v character
#. Use the arrow keys to select the lines
#. press `:`
#. type `s/^#//`
#. press enter

Indenting
##############

#. Move the cursor to the beginning of the section you want to comment out
#. Press uppercase V to enter **visual line mode**
#. let go of the v character
#. Use the arrow keys to select the lines
    #. Press the `>` to indent
    #. Press the '<' to unindent

Replace multiple matching words at once
################################################

.. code-block:: console

    :%s/oldword/newword/gc

* the `%` means it is applied to the entire file
* the `s/oldword/newword/g` means it subsitutes the oldword for the newword globally
* the `c` at the end means it will prompt for confirmation before each change


Add a certain string to the end of each line
####################################################

.. code-block:: console

    :%s/$/.hogwarts.edu/

* the `%s` subsitutes on **all lines**
* the `$` matches the **end of each line**
* `.hogwarts.edu` is the text to be added


Removing a ./ from a string
###################################

.. code-block:: console

    :%s#\./##g

* `:%s` → Substitute in all lines
* `\./` → Escapes the literal . and matches ./
* `##` → Replace with nothing (delete it)
* `g` → Global (all matches per line)