Associate Penetration Tester Interview Questions
****************************************************

1. How would get to google if you have a DHCP IP?
####################################################

   You would assign the Defualt Gateway and then receive the IP address.

2. What is the difference between TCP and UDP?
###################################################

TCP is a connection-oriented protocol, whereas UDP is a connectionless protocol. A key difference between TCP and UDP is speed, as TCP is comparatively slower than UDP. Overall, UDP is a much faster, simpler, and efficient protocol, however, retransmission of lost data packets is only possible with TCP.

Another notable discrepancy with TCP vs UDP is that TCP provides an ordered delivery of data from user to server (and vice versa), whereas UDP is not dedicated to end-to-end communications, nor does it check the readiness of the receiver (requiring fewer overheads and taking up less space).  

.. list-table:: TCP v. UDP
   :widths: 25 25 50
   :header-rows: 1

   * - Feature
     - TCP
     - UDP
   * - Connection status
     - Requires an established connection to transmit data (connection should be closed once transmission is complete)
     - Connectionless protocol with no requirements for opening, maintaining, or terminating a connection
   * - Data sequencing
     - Able to sequence
     - Unable to sequence
   * - Guaranteed delivery
     - Can guarantee delivery of data to the destination router
     - Cannot guarantee delivery of data to the destination
   * - Retransmission of data
     - Retransmission of lost packets is possible
     - No retransmission of lost packets
   * - Error checking
     - Extensive error checking and acknowledgment of data
     - Basic error checking mechanism using checksums
   * - Method of transfer
     - Data is read as a byte stream; messages are transmitted to segment boundaries
     - UDP packets with defined boundaries; sent individually and checked for integrity on arrival
   * -  Speed
     - Slower than UDP
     - Faster than TCP
   * - Broadcasting
     - Does not support Broadcasting
     - Does support Broadcasting
   * - Optimal use
     - Used by HTTPS, HTTP, SMTP, POP, FTP, etc
     - Video conferencing, streaming, DNS, VoIP, etc

3. Name 5 different linux terminal commands
#############################################
        * man
        * cat
        * ls
        * less + more
        * cd

4. Where do you view the logs in Linux?
###########################################

/var/log

5. Where do you view the logs in Windows?
############################################

Event Viewer

6. How can you view permissions in Windows
#############################################

        * whoami /all
        * whoami /priv
        * net user <userame>
        * net localgroup

7. What is Active Directory?
#################################

An active directory is a directory structure used on Microsoft Windows based servers and computers to store data and information about networks and domains.

8. What can Active Directory do?
###################################

        * Windows Update Server
        * LDAP/AD Users and Computers
        * DNS
        * DHCP
        * Web Server

9. Explain Symmetric and Asymmetric Encryption?
################################################

Firstly, encryption is changing the order of data’s appearance from its original format to keep out intrusion from those who do not have the clearance to access the data. Symmetric encryption involves the use of a single encryption and decryption pass key. One password can both encrypt and decrypt the data in such cases, and both the owner and end-user share the same key.

In asymmetric encryption, the software owners have a private passkey while the end-users have a public pass key. This is to segregate high-level data that the public cannot access from available data.
