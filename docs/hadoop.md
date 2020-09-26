# **How to Perform Hadoop Forensics**

**How to Perform Hadoop Forensics**

![](RackMultipart20200926-4-1c8o366_html_9ab2864cd8b1e9.jpg)

**Abstract **

Hi peerlysters ! Many modern companies are using [Big data](https://www.peerlyst.com/tags/big-data) to tackle a lot Business issues in a daily basis. This article will teach us the required skills to collect and analyse [Hadoop](https://www.peerlyst.com/tags/hadoop) artifacts.

In this chapter we are going to discover:

- **What is Big Data?**
- **Vs of Big Data**
- **Hadoop overview**
- **Hadoop Architecture**
- **The Hadoop Distributed File System ( HDFS ) **
- **Hadoop Security **
- **Hadoop Forensics**
- **Collecting Hadoop Distributed File System Data **
- **Collecting Hadoop Application Data **
- **Performing Hadoop Distributed File System Analysis**

You can [download](https://www.peerlyst.com/tags/download) this document to find some useful [resources](https://www.peerlyst.com/tags/resources) about Hadoop: [Hadoop Resources](https://static.peerlyst.com/image/upload/v1524347924/post-attachments/Hadoop_Resources_qracya.pdf)

**What is Big Data? **

![](RackMultipart20200926-4-1c8o366_html_5f8e46e35a750496.png)

Big data is a term that describes the large volume of data – both structured and unstructured – that inundates a business on a day-to-day basis. But it&#39;s not the amount of data that&#39;s important. It&#39;s what organizations do with the data that matters. Big data can be analyzed for [insights](https://www.peerlyst.com/tags/insights) that [lead](https://www.peerlyst.com/tags/lead) to better decisions and [strategic](https://www.peerlyst.com/tags/strategic) business moves. [Source : [www.sas.com](http://www.sas.com/) ]

When it comes to data we have 3 categories of it :

- Structured Data : This type of data is stored and processed in well defined format with a fixed schema (about  **20%**  of the total existing data)
- Semi-Structured Data : This Data are not structured but it have some organizational properties to process it in an easy way using for example NoSQL .
- Unstructured Data : This type of Data have no clear format such as Text Files , images, audios, videos.

![](RackMultipart20200926-4-1c8o366_html_14ab91b9867739a6.png)

**The four Vs of Big Data **

- **VOLUME :**  it refers to the volume of collected data from the different sources in an [organization](https://www.peerlyst.com/tags/organization)
  - Youtube : 300 hours of [video](https://www.peerlyst.com/tags/video) are uploaded every minute.
- **VELOCITY : ** it refers to the speed of processing and generating data .
  - Google: 40,000 [search queries](https://www.peerlyst.com/tags/search-queries) every second,
- **VARIETY : ** it refers to the fact that data comes in many types of formats
- **VERACITY : ** It refers to the uncertainty of Data

![](RackMultipart20200926-4-1c8o366_html_60327c0ea330ac1b.png)

**Hadoop overview **

![](RackMultipart20200926-4-1c8o366_html_eaee8ed43b0c88dd.png)

Hadoop is an [open source](https://www.peerlyst.com/tags/open-source) [project](https://www.peerlyst.com/tags/project) that is used to store and [process](https://www.peerlyst.com/tags/process) data in distributed environments. Big data professionals can use from a single to thousands of clusters. Hadoop project is written in java. Some of Hadoop features are :

- _ **Scalability** _
- _ **Reliability** _
- _ **Flexibility** _

To install Hadoop you need to make sure that java is already installed. To check if java is installed just type : java -version

![](RackMultipart20200926-4-1c8o366_html_51150e4dc8868324.png)

Download Hadoop package using &quot;wget&quot; [linux](https://www.peerlyst.com/tags/linux) utility

**wget ** [**http://apache.claz.org/hadoop/common/hadoop-2.7.3**](http://apache.claz.org/hadoop/common/hadoop-2.7.3)

Extract the file with :

**# tar xzf hadoop-2.73.tar.gz**

To set Hadoop [environment variables](https://www.peerlyst.com/tags/environment-variables) (In a single cluster) configure the   **~/.bashrc**

**export HADOOP\_HOME=/usr/local/hadoop**

**Hadoop Architecture **

[Apache](https://www.peerlyst.com/tags/apache) Hadoop [Ecosystem](https://www.peerlyst.com/tags/ecosystem) is composed by the following components:

- **Zookeeper : ** is responsible for coordination
- **Oozie : ** is responsible for the [workflow](https://www.peerlyst.com/tags/workflow) and scheduling
- **Pig : ** it is used for scripting
- **Mahout : ** is responsible for [Machine learning](https://www.peerlyst.com/tags/machine-learning) [operations](https://www.peerlyst.com/tags/operations)
- **Hive :**  is an [SQL](https://www.peerlyst.com/tags/sql) [interface](https://www.peerlyst.com/tags/interface) (Hive Queries)
- **MapReduce :**  is the [distributed processing](https://www.peerlyst.com/tags/distributed-processing) [framework](https://www.peerlyst.com/tags/framework)
- **HDFS :**  it refers to the Hadoop Distributed [file system](https://www.peerlyst.com/tags/file-system)
- **HBase : ** it is a NoSQL [database](https://www.peerlyst.com/tags/database)
- **Sqoop/REST/ODBC : ** for data [integration](https://www.peerlyst.com/tags/integration)

The following graph illustrates the different components of Apache Hadoop ecosystem :

![](RackMultipart20200926-4-1c8o366_html_4068338f062abb22.jpg)

**The Hadoop Distributed File System ( HDFS ) **

The Hadoop Distributed File System ( HDFS ) is taking care of the [storage](https://www.peerlyst.com/tags/storage) in Apache Hadoop. [MapReduce](https://www.peerlyst.com/tags/mapreduce) is consuming data from the HDFS. We can interact with HDFS using a [command line](https://www.peerlyst.com/tags/command-line) interface. HDFS is reliable and fast in addition of giving the power of replicating data to save you in data loss. HDFS is respecting the master-slave architecture. It is composed by the following Nodes:

- **Namenodes : They act as the master servers. They manage the the file system namespace in addition of regulating access and other operations like closing, and opening files.**
- **Datanodes :  They manage data in their systems**
- **Blocks : They are file segments**

![](RackMultipart20200926-4-1c8o366_html_52da95e3d8f8ddfe.gif)

**Hadoop Security **

Hadoop is coming loaded with many security features. Basically it contains different layers of security including :

- Perimeter Level Security
- [Authentication](https://www.peerlyst.com/tags/authentication)
- Authorization
- Data Security

![](RackMultipart20200926-4-1c8o366_html_32adf0d7963d1f90.png)

To dive deep into the security concepts of Hadoop i highly recommend the following links:

[1] [Hadoop Security](https://www.peerlyst.com/tags/hadoop-security) Concepts : [https://community.hortonworks.com/articles/102957/hadoop-security-concepts.html](https://community.hortonworks.com/articles/102957/hadoop-security-concepts.html)

[2] Introduction to Hadoop Security : [https://www.cloudera.com/documentation/cdh/5-0-x/CDH5-Security-Guide/cdh5sg\_hadoop\_security\_intro.html](https://www.cloudera.com/documentation/cdh/5-0-x/CDH5-Security-Guide/cdh5sg_hadoop_security_intro.html)

[3] [Big Data Security](https://www.peerlyst.com/tags/big-data-security) and [Privacy](https://www.peerlyst.com/tags/privacy) Handbook : [https://cloudsecurityalliance.org/download/big-data-security-and-privacy-handbook/](https://cloudsecurityalliance.org/download/big-data-security-and-privacy-handbook/)

![](RackMultipart20200926-4-1c8o366_html_1dcc0bcfd61298aa.jpg)

**Hadoop Forensics**

![](RackMultipart20200926-4-1c8o366_html_e1f927a0cf5d6396.jpg)

Big Data [Forensics](https://www.peerlyst.com/tags/forensics) especially Hadoop forensics is the art of locating, collecting and analysing Hadoop artifacts.

Hadoop Forensics goes thru the following steps:

**1- Identification and locating data sources**

**2- Data Collection **

**3- Analysis**

**4- Presenting the findings**

For every data source we need to consider the following criterias:

- **Data quality**
- **Data completeness**
- **Previous storage**
- **How Data enter and leaves**
- **Extraction formats**

As an identification process we can follow these steps:

- **Identifying data requirements**
- **Interviewing the responsible staff **
- **Check systems documentations**
- **Assess data viability**
- **Build data collection plan**

Once evidence is collected, the [chain of custody](https://www.peerlyst.com/tags/chain-of-custody) [documentation](https://www.peerlyst.com/tags/documentation) needs to be established.

&quot; **Chain of custody**  (CoC), in legal contexts, refers to the chronological documentation or paper trail that records the sequence of  **custody** , control, transfer, analysis, and disposition of physical or electronic evidence.&quot; [Source Wikipedia]

**Collecting Hadoop Distributed File System Data **

![](RackMultipart20200926-4-1c8o366_html_3bf7e0f07bd6dbd7.jpg)

As discussed before, Data is stored in Hadoop Distributed File System** (**HDFS). To collect data you can take a complete [forensic](https://www.peerlyst.com/tags/forensic)image, Make a logical copy of all HDFS files and directories or select a targeted files.Investigators can collect data from a single machine while preserving the [metadata](https://www.peerlyst.com/tags/metadata) by connecting to a Hadoop client because collecting images of every cluster is time consuming operation. The [data collection](https://www.peerlyst.com/tags/data-collection) can be physical or remotely. Also [investigators](https://www.peerlyst.com/tags/investigators) can collect data through the [host](https://www.peerlyst.com/tags/host)[operating system](https://www.peerlyst.com/tags/operating-system) by imaging the host operating system and capturing Hadoop configuration files like  **/etc/hadoop/hdfs-site.xml ** and  **dfs.data.dir ** located in /var/hadoop/datanode that contains the value of the DataNode. For the imaging operation you can use **EnCase and Forensic Toolkit (FTK)**

To get information about cluster using the [browser](https://www.peerlyst.com/tags/browser) link you can visit:

\&lt;address\&gt;:50070/dfshealth.html

or you can type :  **hdfs dfsadmin -report ** via the command line

Edit log can be a source for meta-data: The following operation can be logged:

▪ OP\_INVALID
 ▪ OP\_ADD
 ▪ OP\_RENAME\_OLD
 ▪ OP\_DELETE
 ▪ OP\_MKDIR
 ▪ OP\_SET\_REPLICATION
 ▪ OP\_DATANODE\_ADD
 ▪ OP\_DATANODE\_REMOVE
 ▪ OP\_SET\_PERMISSIONS
 ▪ OP\_SET\_OWNER
 ▪ OP\_CLOSE
 ▪ OP\_SET\_GENSTAMP
 ▪ OP\_SET\_NS\_QUOTA
 ▪ OP\_CLEAR\_NS\_QUOTA
 ▪ OP\_TIMES
 ▪ OP\_SET\_QUOTA
 ▪ OP\_RENAME
 ▪ OP\_CONCAT\_DELETE
 ▪ OP\_SYMLINK
 ▪ OP\_GET\_DELEGATION\_TOKEN
 ▪ OP\_RENEW\_DELEGATION\_TOKEN
 ▪ OP\_CANCEL\_DELEGATION\_TOKEN
 ▪ OP\_UPDATE\_MASTER\_KEY
 ▪ OP\_REASSIGN\_LEASE
 ▪ OP\_END\_LOG\_SEGMENT
 ▪ OP\_START\_LOG\_SEGMENT
 ▪ OP\_UPDATE\_BLOCKS

![](RackMultipart20200926-4-1c8o366_html_de21163e40ecd47b.jpg)

**Collecting Hadoop Application Data **

Collecting Hadoop Application data. Data in hadoop can be accessed by many different applications.Investigators can use many methods including:

- Backup-based collection
- Query-based collection
- Script-based collection
- Software-based collection

For example to identify Hive Evidence you can use the following HiveQL commands:

- SHOW DATABASES;
- SHOW TABLES;
- USE databaseName;
- DESCRIBE (FORMATTED|EXTENDED) table;

The following [script](https://www.peerlyst.com/tags/script) is developed by  **Joe Sremack ** to create a connection to Hive and exports the results.

import pyhs2

import datetime

outputFile = open(&#39;/home/extract/outputFile.txt&#39;, &#39;w&#39;)

logFile = open(&#39;/home/extract/logFile.txt&#39;, &#39;w&#39;)

logFile.write(str(datetime.date.today())+&#39;\n&#39;)

with pyhs2.connect(host=&#39;localhost&#39;,

port=10000,

authMechanism=&quot;PLAIN&quot;,

user=&#39;root&#39;,

password=&#39;pwdVal&#39;,

database=&#39;default&#39;) as conn:

with conn.cursor() as cur:

logFile.write(cur.getDatabases()+&#39;\n&#39;)

cur.execute(&quot;select \* from table&quot;)

logFile.write(&#39;select \* from table\n&#39;)

logFile.write(&#39;Number of rows: &#39; + str(cur.rowcount) + &#39;\n&#39;)

logFile.write(cur.getSchema()+&#39;\n&#39;)

#Fetch table results

for i in cur.fetch():

outputFile.write(i + &#39;\n&#39;)

outputFile.close()

logFile.close()

**Performing Hadoop Distributed File System Analysis **

To perform Hadoop Distributed File System Analysis a well defined process should be followed. The investigator should apply these steps:

**1- Forming hypothesis**

**2- Analysis plan developing**

**3- Analysis performing**

**4- Result assessing **

**5- Modifying findings**

During the analysis you can face some challenges such as : [Data encryption](https://www.peerlyst.com/tags/data-encryption) and anti-forensics techniques.

**Further Readings **

1 - I highly recommend reading this book  **&quot; Big Data Forensics – Learning Hadoop Investigations &quot; **. It was the main reason that made me write this article. You can find a preview by visiting this link : [https://books.google.tn/books/about/Big\_Data\_Forensics\_Learning\_Hadoop\_Inves.html?id=lrZrCgAAQBAJ&amp;printsec=frontcover&amp;source=kp\_read\_button&amp;redir\_esc=y#v=onepage&amp;q&amp;f=false](https://books.google.tn/books/about/Big_Data_Forensics_Learning_Hadoop_Inves.html?id=lrZrCgAAQBAJ&amp;printsec=frontcover&amp;source=kp_read_button&amp;redir_esc=y#v=onepage&amp;q&amp;f=false)

![](RackMultipart20200926-4-1c8o366_html_d616b8151ca71a85.jpg)

**2 - The Human Face of Big Data : ** [**http://amzn.to/2iDZgBt**](http://amzn.to/2iDZgBt)

![](RackMultipart20200926-4-1c8o366_html_7fbe5c07cdf6ed8c.jpg)

**3 - The Signal and the Noise: Why So Many Predictions Fail – But Some Don&#39;t : ** [**http://amzn.to/2iE4opv**](http://amzn.to/2iE4opv)

![](RackMultipart20200926-4-1c8o366_html_b5b810f3c8c5c797.jpg)

4 -  **Hadoop: The Definitive Guide : ** [**http://amzn.to/2hTYHo4**](http://amzn.to/2hTYHo4)

![](RackMultipart20200926-4-1c8o366_html_efeadc0f291b6ed9.gif)

**5 - Big Data &amp; Analytics Tutorials : ** [**https://www.tutorialspoint.com/big\_data\_tutorials.htm**](https://www.tutorialspoint.com/big_data_tutorials.htm)

**6 - Free Hadoop Tutorial: Master Big Data : ** [**https://www.guru99.com/bigdata-tutorials.html**](https://www.guru99.com/bigdata-tutorials.html)

**7 - Big Data Tutorial: All You Need To Know About Big Data ! : ** [**https://www.edureka.co/blog/big-data-tutorial**](https://www.edureka.co/blog/big-data-tutorial)

**8 - Hadoop Tutorial: All you need to know about Hadoop ! : ** [**https://www.edureka.co/blog/hadoop-tutorial/**](https://www.edureka.co/blog/hadoop-tutorial/)

**9 - Securing HDFS, Hive and HBase with Knox and Ranger - Hortonworks : ** [**https://hortonworks.com/hadoop-tutorial/manage-security-policy-hive-hbase-knox-ranger/**](https://hortonworks.com/hadoop-tutorial/manage-security-policy-hive-hbase-knox-ranger/)

**10 -  Hadoop tutorial: How to Refine and Visualize Server Log Data : ** [**Hadoop tutorial: How to Refine and Visualize Server Log Data**](https://hortonworks.com/hadoop-tutorial/how-to-refine-and-visualize-server-log-data/)

**Summary **

By now, we acquired a [fair](https://www.peerlyst.com/tags/fair) understanding about Hadoop internals and HDFS. We learned [how to](https://www.peerlyst.com/tags/how-to) collect data from Hadoop and how to analyse them in order to perform Hadoop Forensics.

**Post Updates**

**\* \* \* **

**References used in this Article (including sources of Graphs and illustrations):**

[1]  **Big Data Forensics – Learning Hadoop Investigations - Packt Publishing Ltd. : ** [https://books.google.tn/books/about/Big\_Data\_Forensics\_Learning\_Hadoop\_Inves.html?id=lrZrCgAAQBAJ&amp;printsec=frontcover&amp;source=kp\_read\_button&amp;redir\_esc=y#v=onepage&amp;q&amp;f=false](https://books.google.tn/books/about/Big_Data_Forensics_Learning_Hadoop_Inves.html?id=lrZrCgAAQBAJ&amp;printsec=frontcover&amp;source=kp_read_button&amp;redir_esc=y#v=onepage&amp;q&amp;f=false)

[2]  **Big Data Tutorial: All You Need To Know About Big Data ! : ** [https://www.edureka.co/blog/big-data-tutorial](https://www.edureka.co/blog/big-data-tutorial)

[3]  **Big Data What it is and why it matters : ** [https://www.sas.com/en\_us/insights/big-data/what-is-big-data.html](https://www.sas.com/en_us/insights/big-data/what-is-big-data.html)

[4]  **The 10 Vs of Big Data : ** [https://tdwi.org/articles/2017/02/08/10-vs-of-big-data.aspx](https://tdwi.org/articles/2017/02/08/10-vs-of-big-data.aspx)

[5]  **Big data: changing the way businesses compete and operate : ** [http://www.ey.com/gl/en/services/advisory/ey-big-data-big-opportunities-big-challenges](http://www.ey.com/gl/en/services/advisory/ey-big-data-big-opportunities-big-challenges)

[6]   **Hadoop - Environment Setup : ** [https://www.tutorialspoint.com/hadoop/hadoop\_enviornment\_setup.htm](https://www.tutorialspoint.com/hadoop/hadoop_enviornment_setup.htm)

[7]  **How to Install Hadoop in Stand-Alone Mode on Ubuntu 16.04 : ** [https://www.digitalocean.com/community/tutorials/how-to-install-hadoop-in-stand-alone-mode-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-hadoop-in-stand-alone-mode-on-ubuntu-16-04)

[8]  **Chain of custody - Wikipedia : ** [https://en.wikipedia.org/wiki/Chain\_of\_custody](https://en.wikipedia.org/wiki/Chain_of_custody)

[9]  **Hadoop Forensics : Be in a defensible position. Be cyber resilient - Kevvie Fowler , GCFA Gold, CISSP -National Cyber Response Leader - KPMG Canada**
