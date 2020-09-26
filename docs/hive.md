A practical Guide: How to Install and use The Hive Project in Incident Management

Hi Peerlysters,

In this article, we are going to explore a great incident management platform called &quot;TheHive Project.&quot;

![](RackMultipart20200926-4-111dfwc_html_688ee9f417e8f571.png)

[Figure](https://blogthehiveproject.files.wordpress.com/2017/12/case3.png)

**What are attack vectors? **

Attack vectors are the paths used by attackers to access a vulnerability. In other words, the method used to attack an asset is called a  **Threat Vector**  or  **Attack vector. ** Attack vectors can be analysed. The analysis is done by studying the attack surfaces like the entry points of an application, APIs, files, databases, user interfaces and so on. When you face a huge number of entries you can divide the modeling into different categories (APIs, Business workflows etc...)

_The National Institute of Standards and Technology ( NIST )_ believes that _Organizing an effective computer security incident response capability (CSIRC) involves several major decisions and actions. One of the first considerations should be to create an organization Specific definition of the term &quot;incident&quot; so that the scope of the term is clear. The organization should decide what services the incident response team should provide, consider which team structures and models can provide those services, and select and implement one or more incident response teams. Incident response Plan, Policy, and procedure creation is an important part of establishing a team, so that incident Response is performed effectively, efficiently, and consistently, and so that the team is empowered to do what needs to be done. _

**But What is an information security Incident?**

An  **event**  is any observable occurrence in a system or network. Events include a user connecting to a file share, a server receiving a request for a web page, a user sending email, and a firewall blocking a connection attempt. Adverse events are events with a negative consequence, such as system crashes, packet floods, unauthorized use of system privileges, unauthorized access to sensitive data, and execution of malware that destroys data.

The following are some security incidents:

- Information theft
- Unauthorized access to systems
- Denial-of-service (DoS) attacks
- Ransomware attacks

**Incident response process **

Incident response like any methodological operation goes through a well defined number of steps:

- **Preparation:**  during this phase, the teams deploy the required tools and resources to successfully handle the incidents including developing awareness trainings.
- **Detection and analysis: ** this is the most difficult phase.It is a challenging step for every incident response team. This phase includes networks and systems profiling,log retention policy,signs of an incident recognition and prioritizing security incidents.
- **Containment eradication and recovery: ** during this phase the evidence pieces are collected and the containment and recovery strategies are maintained.
- **Post incident activity: ** discussions are held during this phase to evaluate the team performance, to determine what actually happened, policies compliance and so on.

![](RackMultipart20200926-4-111dfwc_html_1cfcd2a94b48658e.png)

[Figure](https://www.exabeam.com/wp-content/uploads/2018/09/IR-plan-steps.png)

**Sources of Security Events **

During incident response operation there are a lot of artifacts resources you need to collect. You can use different artifacts such as:

- IP addresses
- Domain names
- URLs
- System calls
- Processes
- Services and ports
- File hashes

**Establishing Incident Response Teams **

There are different incident response Teams: Computer Security Incident Response Teams, Product Security Incident Response Teams and National CSIRTs and Computer Emergency Response Teams. Let&#39;s discover them one by one.

**Computer Security Incident Response Teams (CSIRTs) **

Computer Security Incident Response Teams (CSIRTs) are working in collaboration with the information security team. Usually, they receive security breach reports and conduct the required analysis. The team may contain: a Manager, triage staff, Vulnerability handlers, Incident handlers, Artifact analysis staff and other members. To establish your Computer Security Incident Response Team you need to:

- Defining the CSIRT constituency
- Ensuring management and executive support
- Making sure that the proper budget is allocated
- Deciding where the CSIRT will reside within the organization&#39;s Hierarchy
- Determining whether the team will be central, distributed, or virtual.
- Developing the process and policies for the CSIRT.

**Product Security Incident Response Teams (PSIRTs) **

Product Security Incident Response Teams (PSIRTs) are responsible for managing the receipt, investigation and internal coordination of security vulnerability information related to a product of the company (including offerings, solutions, components and services)

**National CSIRTs and Computer Emergency Response Teams (CERTs) **

Many countries establish their own incident response teams like  **US-CERT | United States Computer Emergency Readiness Team**. Computer emergency response teams are responsible for:

- Providing cybersecurity protection to Federal civilian executive branch agencies through intrusion detection and prevention capabilities.
- Responding to incidents and analyzing data about emerging cyber threats.
- Collaborating with foreign governments and international entities to enhance the nation&#39;s cybersecurity posture.

**The Hive Project**

According to its official Github [repository](https://github.com/TheHive-Project/TheHiveDocs):

![](RackMultipart20200926-4-111dfwc_html_f7bc7bbdc53aa405.png)

[Figure](https://github.com/TheHive-Project/TheHiveDocs/raw/master/images/thehive-logo.png)

&quot;TheHive is a scalable 4-in-1 open source and free security incident response platform designed to make life easier for SOCs, CSIRTs, CERTs and any information security practitioner dealing with security incidents that need to be investigated and acted upon swiftly. Thanks to [Cortex](https://github.com/TheHive-Project/Cortex/), our powerful free and open-source analysis engine, you can analyze (and triage) observables at scale using more than 100 analyzers.&quot;

To deploy the project you need these hardware requirements:

- _8vCPU_
- _8 GB of RAM_
- _60 GB of disk_

Now let&#39;s explore how to install the project:

First, you need to install Java:

sudo ** apt-get install openjdk-11-jre-headless**

Add the sources:

**echo &#39;deb ** [**https://dl.bintray.com/thehive-project/debian-stable**](https://dl.bintray.com/thehive-project/debian-stable) ** any main&#39; | sudo tee -a /etc/apt/sources.list.d/thehive-project.list**

**curl ** [**https://raw.githubusercontent.com/TheHive-Project/TheHive/master**](https://raw.githubusercontent.com/TheHive-Project/TheHive/master) ** /PGP-PUBLIC-KEY | sudo apt-key add -**

Update the system:

sudo apt-get update

**Install Elasticsearch**

![](RackMultipart20200926-4-111dfwc_html_5b0d48abd3e12cf4.png)

[Figure](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQYUtxYVLaTMM9-M_XRxd0QNpS8PS32iGM5Ukg91_WHmV4nSaRG&amp;s)

**apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key D88E42B4**

**echo &quot;deb ** [**https://artifacts.elastic.co/packages/5.x/apt**](https://artifacts.elastic.co/packages/5.x/apt) ** stable main&quot; | tee -a/etc/apt/sources.list.d/elastic-5.x.list**

**apt install apt-transport-https**

**apt update**

**sudo apt install elasticsearch**

Install &quot;The Hive&quot;

sudo apt-get install thehive

sudo mkdir /etc/thehive

(cat \&lt;\&lt; \_EOF\_
 # Secret


 class=&quot;mention&quot;
 data-id=&quot;dZh72HAdp6kxuKvmP&quot;
 data-type=&quot;Tag&quot;
 href=&quot;/tags/key&quot;\&gt;key

 #
 ~~~~~

 #
 The
 secret

key
 is
 used
 to


 class=&quot;mention&quot;
 data-id=&quot;5qfRhdsxtZYahMQG8&quot;
 data-type=&quot;Tag&quot;
 href=&quot;/tags/secure&quot;\&gt;secure
 cryptographics
 functions.

 #
 If
 you
 deploy
 your
 application
 to
 several
 instances
 be
 sure
 to

 use
 the
 same
 key!

 play.http.secret.key=&quot;\&lt;ADD
 A
 RANDOM
 STRING
 HERE\&gt;&quot;

 \_EOF\_

 )
 |
 sudo
 tee
 -a
 /etc/thehive/application.conf

sudo systemctl enable thehive

 sudo

 class=&quot;mention&quot;
 data-id=&quot;5iDGsM3BLteuqonai&quot;
 data-type=&quot;Tag&quot;
 href=&quot;/tags/service&quot;\&gt;service
 thehive
 start

Now go to your browser and type:

[http://YOUR\_SERVER\_ADDRESS:9000/](http://your_server_address:9000/)

If you want to try it before installing it on your server you download the training VM. You can find it here:

[https://drive.google.com/file/d/1KXL7kzH7Pc2jSL2o1m1\_RwVc3FGw-ixQ/view](https://drive.google.com/file/d/1KXL7kzH7Pc2jSL2o1m1_RwVc3FGw-ixQ/view)

Once you download it, open it with your virtual machine

![](RackMultipart20200926-4-111dfwc_html_1885fde9f3303023.png)

My local IP address is ** 192.168.43.188**. Then to enter TheHive I need to use this URL:   **192.168.43.188:9000**

To access the platform use these credentials:

- **Login: ** admin
- **Password: ** thehive1234

![](RackMultipart20200926-4-111dfwc_html_9d660280b6418deb.png)

Voila! You are in the main dashboard

![](RackMultipart20200926-4-111dfwc_html_8acfb3302dd97c50.png)

Let&#39;s start exploring how to use TheHive.

**Users**

To create add your team members you need to create users. To create a user go to  **Admin -\&gt; Users** :

![](RackMultipart20200926-4-111dfwc_html_2eac10a2b56fc349.png)

Click on &quot;Add user&quot;

![](RackMultipart20200926-4-111dfwc_html_bee9290b60a06ff5.png)

Add your user information

![](RackMultipart20200926-4-111dfwc_html_7b78bcb68db740e5.png)

The user was added successfully

![](RackMultipart20200926-4-111dfwc_html_95239e3977d7e434.png)

Create a new password for it by clicking &quot; **New password**&quot;, type a password and press enter to save it.

Our password will be &quot; **analyst1**&quot; too.

**Cases: **

To create cases in the Hive, click on &quot; **New case&quot;**

![](RackMultipart20200926-4-111dfwc_html_b0a500abce1427f5.png)

Add your case information:

- _Title_
- _Severity: Low, Medium or High_
- _Date_
- _Tags and so on. _

Add the case tasks:

![](RackMultipart20200926-4-111dfwc_html_b6f59922998b1b25.png)

Now we created a case file

![](RackMultipart20200926-4-111dfwc_html_56d3d05b0035ce29.png)

The case file contains also the tasks and the Observables:

![](RackMultipart20200926-4-111dfwc_html_6fa508e5ab036a0f.png)

You will find the case in the &quot;Waiting cases&quot; section

![](RackMultipart20200926-4-111dfwc_html_efacf467398cb931.png)

 To take it just click on tasks and it will be added to your &quot;my tasks&quot; section

![](RackMultipart20200926-4-111dfwc_html_8940c984c86e24.png)

Once you finish the case, click on &quot;Close&quot; and it will be closed

**Dashboards**

To visualize your cases statistics you need to use The Hive dashboards. To open or create a new dashboard go to &quot;Dashboards&quot;

![](RackMultipart20200926-4-111dfwc_html_4ba24c6921f0366.png)

Select any available dashboard to explore it

![](RackMultipart20200926-4-111dfwc_html_88e1d0dd31a4e6e0.png)

![](RackMultipart20200926-4-111dfwc_html_ea5a9a78b21f6365.png)

**Cortex:**

![](RackMultipart20200926-4-111dfwc_html_7a59c8f1bb25d19b.png)

Its developers define cortex as follows:

&quot;Thanks to Cortex, observables such as IP and email addresses, URLs, domain names, files or hashes can be analyzed using a Web interface. Analysts can also automate these operations and submit large sets of observables from TheHive or through the Cortex REST API from alternative SIRP platforms, custom scripts or MISP. When used in conjunction with TheHive, Cortex largely facilitates the containment phase thanks to its Active Response features.&quot;

The following graph illustrates Cortex architecture:

![](RackMultipart20200926-4-111dfwc_html_ad2dfd25a305fa45.png)

[Figure](https://github.com/TheHive-Project/Cortex/raw/master/images/Architecture.png)

To enter cortex type this address on your browser: http://YOUR\_SERVER\_ADDRESS:9001/

Login to cortex using the same credentials as The hive

- Login: admin
- Password: thehive1234

![](RackMultipart20200926-4-111dfwc_html_2dd700cdba848758.png)

This is the main dashboard of &quot;Cortex&quot;

![](RackMultipart20200926-4-111dfwc_html_148bb3842d97d1a0.png)

**Summary **

In this guide, we explored some important terminologies in incident response. Later, we discovered a great incident management platform called &quot;the Hive&quot; where we saw how to install it and use it to manage your team cases.

To learn more about Incident Response you can download this document that contains many useful resources: [Incident response Resources](https://static.peerlyst.com/image/upload/v1576272434/post-attachments/Incident_response_Resources_ekm5eu)

Your comments are playing a huge role in this article. Please if you want to add or correct something please don&#39;t hesitate to comment so we can create together a one stop resource for readers who are looking for a guide to learn about The Hive Project. All your comments are welcome!

**References: **

- [How to Handle Information Security Incidents [Part 1]](https://www.peerlyst.com/posts/how-to-handle-information-security-incidents-part-1-chiheb-chebbi?trk=search_page_search_result)
-  Recommendations of the National Institute of Standards and Technology: Computer Security Incident Handling Guide: [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-61r2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-61r2.pdf)
-  Computer Security Incident Response Team (CSIRT) : [http://whatis.techtarget.com/definition/Computer-Security-Incident-Response-Team-CSIRT](http://whatis.techtarget.com/definition/Computer-Security-Incident-Response-Team-CSIRT)
-  US-CERT | United States Computer Emergency Readiness Team : [https://www.us-cert.gov/about-us](https://www.us-cert.gov/about-us)
