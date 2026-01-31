Administer Tab
******************

Creating an organization
################################

GUI
----------

#. Click Administer
#. Click organization
#. Click New organization
 #. The organization name and label can be the same
#. click submit

CLI
---------

.. code-block:: console

    hammer organization list
    hammer organization create --name "Hogwarts IT" --label "hogwarts_it" --description "Hogwarts IT Department"
    hammer user update --login admin --organization "Hogwarts IT"
    hammer location add-organization --name "North America" --organization "Hogwarts IT"


Editting the organization
###############################

GUI
---------

* Capsules
 * select the correct capsules to use
* Media
  * test
* domains
 * add the domain needed
* Host Groups
 * add the host groups needed
* Locations
 * add the locations needed
