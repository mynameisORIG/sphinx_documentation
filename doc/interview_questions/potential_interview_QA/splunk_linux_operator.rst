Potential Splunk Linux Operator interview questions
**********************************************************

https://www.upgrad.com/blog/splunk-interview-questions-answers-beginners-experienced/

1. What Is Splunk, and How Does It Work?
###############################################

Splunk is a real-time data analytics platform that ingests machine-generated data from various sources like:

* logs
* metrics
* applications

It indexes this data into searchable events, enabling powerful querying, monitoring, and visulization through tis Search Processing language (SPL)

2. Can you Explain the Key Components of Splunk's Architecture?
#######################################################################

* Forwarders
 * collect and send data
* Indexers
 * store and index Data
* Search Heads
 * allow users to search and visualize

3. What are the different types of splunk forwarders, and how do they function
########################################################################################

* Universal Forwarders (UF)
 * lightweight; send raw data
 * installed on endpoints, servers, or applications
* Heavy Forwarders
 * processes and filters data before forwarding
* Intermediate Forwarders
 * placed between other forwarders and Indexers
 * used for load balancing, centeralized routing, or traffic control

Each server different data collection needs, ensuring flexible and efficent data ingestion across varied environments.

4. Which Port Numbers are Commonly Used by Splunk
#######################################################

* **8089** for management
 * UNCSO uses 8900
* **9997** for data forwarding
* **8000** for web interface
* **514** for syslog

6. What are the different types of Splunk Licenses available
######################################################################


* Enterprise License
 * Unlimited indexing with full features.
* Free License
 * Limited to 500MB/day with reduced functionality.
* Trial License
 * Temporary access to Enterprise features.
