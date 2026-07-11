Notifcations
*********************************************

Notifcations are a way in nagios to send information is something is wrong.

Host Contact Groups
################################

This should show you the Hosts where if the Host had warnings, it should show you the contact group.

.. code-block:: console

    grep -ri 'contact_groups' /usr/local/nagios/etc/hosts/*

Services Contact Groups
################################

This should show you the Hosts where if the Host had warnings, it should show you the contact group.

.. code-block:: console

    awk '
    /^define service/,/^}/ {
        if ($1 == "host_name") hn = $2;
        else if ($1 == "service_description") sd = $2;
        else if ($1 == "contact_groups") cg = $2;
        else if ($1 == "}") {
            print hn "\t" sd "\t" cg;s
            hn = sd = cg = "";
        }
    }' /usr/local/nagios/etc/services/*
