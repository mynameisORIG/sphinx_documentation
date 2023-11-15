Wireshark tips
****************

Find SAMBA version
######################

1. Open Wireshark
2. Select the Port (tun0, wlan0)
3. Run 'smbclient -NL //<RHOST>
4. Press Ctrl-f
5. change to string and search to Session Setup
        5.1 Make Sure to look for Session Setup Andx Response
6. Click the packet
7. Go to SMB -> Session Setup Andx Response -> Action
        7.1 Native LAN Manager should have the samba version
