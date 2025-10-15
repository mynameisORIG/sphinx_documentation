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

9. What is a Summary Index in Splunk, and How is it Used?
#################################################################

A Summary Index in Splunk stores precomputed results from searches, making repeated queries faster. It's userful for tren analysis and reporting where real-time data is not required. For Instance, summarizing daily log volumes help reduce search load

10. What is splunk db connect, and how does it work?
#########################################################

Splunk DB Connect is a plugin that integrates relational databases with Splunk. It allows SQL-based data extraction and joins it with machine data. This unified view supports deeper analytics, like correlatin transactional data with server logs.

11. What are Buckets in Splunk, and Can you Explain the Bucket Lifecycle?
################################################################################

Buckets in Splunk are storage directories that contain indexed data. They pass through distinct lifecycle stages:

* **Hot**: Data is actively written.
* **Warm**: Data is no longer actively written but frequently accessed.
* **Cold**: Archived data, accessed occasionally.
* **Frozen**: Data is either deleted or archived externally.

This lifecycle ensures efficient storage management and quick data retrieval.

12. What type of dashboards can be created in splunk?
############################################################

* **Real-Time Dashboards**: Display live-streaming data.
* **Static Dashboards**: Present a fixed data snapshot for a given timeframe.
* **Interactive Dashboards**: Offer user-driven filtering and drill-down capabilities.

Dashboards enhance visibility and enable quick, actionable insights across datasets.

13. What are the Different Search Modes Supported in Splunk?
###################################################################

* **Fast**: Prioritizes speed; omits some event details
* **Smart**: Balances speed and depth by adapting to query complexity.
* **Verbose**: Provides complete event information, including raw data.

Search mode selection directly afects performance and data granularity.