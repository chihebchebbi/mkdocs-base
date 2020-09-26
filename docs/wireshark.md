Hands-on Malicious Traffic Analysis with Wireshark

Hi Peerlysters,

Communication and networking are vital for every modern organization. Making sure that all the networks of the organization are secure is a key mission.In this article we are going to learn how to analyze malicious traffic using the powerful tool Wireshark.

![](RackMultipart20200926-4-1kxbamy_html_31d8ab112fd2c498.jpg)

[Image Courtesy](https://www.armytimes.com/resizer/tMz7-pZbYe8WTbhGlVTCpaSDtDU=/1200x0/filters:quality(100)/arc-anglerfish-arc2-prod-mco.s3.amazonaws.com/public/SPQTUFFMHRFI7FZBGH36NHJ5MA.jpg)

Before diving deep into traffic analysis,  I believe that we need to explore some networking fundamentals first. It is essential to learn how a network works. Networking is the process of changing information between different devices. The transmission is usually done using a transmission mode. In communications we have generally 3 transmission modes:

- **Simplex Mode:**  in this mode the data is transferred in one direction like the transmission used in TV broadcasting
- **Half-duplex Mode:**  in this mode the data flows in two directions but using a single mean of communication
- **Full-duplex Mode:**  in this mode the data flow is bidirectional and simultaneous.

When it comes to communication networks we have many types. Some of them are the following:

- **Local Area Network (LAN):** this network is used in small surfaces and areas
- **Metropolitan area network (MAN): **this network is larger than the Local Area Network. We can use for example to connect two offices.
- **Wide area network (WAN): **We use this type of networks to connect large distances
- **Personal area network (PAN): **this network is used in short distances and small areas like a single room.

**Network Topologies**

A topology is a schematic representation of a network. You can see it as the layout of the network and how the connected devices are arranged in the network. In networking we have many topologies some of the them are:

- **Ring Topology:  ** the data flows in one direction
- **Star Topology:  ** all the devices are connected to a single node (Hub)
- **Tree Topology: ** this topology is hierarchical
- **Bus Topology: ** all the devices are connected to a central connection
- **Fully-connected Topology:**  each device is connected with all the other devices of the network

**What is a network traffic?**

[Techopedia](https://www.techopedia.com/definition/29917/network-traffic) defines it as follows:

&quot;_Network traffic refers to the amount of data moving across a network at a given point of time.  __Network data__  is mostly encapsulated in  __network packets__ , which provide the load in the network.  __Network traffic__  is the main component for network traffic measurement, network traffic  __control__  and simulation.&quot;_

![](RackMultipart20200926-4-1kxbamy_html_16c516d85efb846f.png)

[Image Courtesy](https://www.flowmon.com/getattachment/Solutions/use-case/flow-monitoring/product-img_Monitoring.png.aspx?width=480&amp;height=309)

**Traffic Analysis with Wireshark **

![](RackMultipart20200926-4-1kxbamy_html_f6c1567191def229.png)

The most suitable tool that will help you analyze your network traffic is definitely Wireshark. Wireshark is a free and open-source tool to help you analyse network protocols with deep inspection capabilities. It gives you the ability to perform live packet capturing or offline analysis. It supports many operating systems including Windows, Linux, MacOS, FreeBSD and many more systems.

You can download it from here: [https://www.wireshark.org/download.html](https://www.wireshark.org/download.html)

_To learn more about it:_

- [How to use Wireshark: Part one](https://www.peerlyst.com/posts/let-s-use-wireshark-part-one-kimberly-crawley?trk=search_page_search_result)
- [How to get started with Wireshark plugins, tools, and scripts](https://www.peerlyst.com/posts/how-to-get-started-with-wireshark-plugins-tools-and-scripts-kimberly-crawley?trk=search_page_search_result)

![](RackMultipart20200926-4-1kxbamy_html_4cd7581317d7669b.png)

Wireshark will help capture and analyze traffic as  **pcap**  files. The analysis follows the OSCAR methodology:

- Obtain
- Strategize
- Collect Evidence
- Analyze
- Report

![](RackMultipart20200926-4-1kxbamy_html_aa6be3f85b03c23f.jpg)

[Image Courtesy](https://ai2-s2-public.s3.amazonaws.com/figures/2017-08-08/127890c2e5d5b14ec6b1671436e2b965f323eda0/3-Figure2-1.png)

Let&#39;s start by analyzing a sample pcap file so we can understand Wireshark capabilities. But before that we need to know an important model called the  **OSI netwoking Model** :

By Definition: &quot;The  **Open Systems Interconnection model**  ( **OSI model** ) is a conceptual model that characterizes and standardizes the communication functions of a telecommunication or computing system without regard to its underlying internal structure and technology. Its goal is the interoperability of diverse communication systems with standard protocols. The model partitions a communication system into abstraction layers. The original version of the model defined seven layers.

In other words data is moving in the network respecting a specific order. The following are the seven Layers of the OSI Model:

7- Application layer

6 -Presentation layer

5- Session layer

4- Transport layer

3- Network layer

2- Data link layer

1- Physical layer

The following graph illustrates the different OSI model layers:

![](RackMultipart20200926-4-1kxbamy_html_5fef5fa7ddc390bb.png)

[Image Courtesy](https://www.researchgate.net/profile/Jay_Johnson3/publication/322568288/figure/fig6/AS:631584889778238@1527592980914/OSI-model-seven-layer-protocol-stack-28.png)

As a first demonstration let&#39;s start analyze a small [pcap](https://www.malware-traffic-analysis.net/training/host-and-user-ID-pcap-01.pcap.zip) delivered by _malware-traffic-analysis.net. _The file password is &quot;_infected_&quot;

Once you open it with Wireshark you will get this main window:

![](RackMultipart20200926-4-1kxbamy_html_404c2788988981f7.png)

Let&#39;s start collecting some helpful information like the Host, destination, source etc...

To get the host we can use the DHCP filter.

Dynamic Host Configuration Protocol (DHCP) is a network layer protocol based on RFC 2131 that enables assigning  IP addresses dynamically to hosts. It goes through 4 steps:

- _Discovery _
- _Offer_
- _Request_
- _Acknowledgment_

![](RackMultipart20200926-4-1kxbamy_html_23dae3ccb7e2f8da.png)

To learn more about Filters check this great resource:_ _[Using Wireshark – Display Filter Expressions](https://unit42.paloaltonetworks.com/using-wireshark-display-filter-expressions/)

Now select: DHCP Request and you will get many helpful pieces of information including the client Mac address. In switching the traffic of data is determined by Media Access Control (MAC) addresses. A MAC address is a unique 48-bit serial number. It is composed equally of the Organizational Unique Identifier (OUI) and the vendor-assigned address.MAC addresses are stored in a fixed size table called the Content Addressable Memory (CAM)

![](RackMultipart20200926-4-1kxbamy_html_c00fdde97b1d1aab.png) And you will get also the hostname. It is &quot;_Rogers-iPad_&quot;

![](RackMultipart20200926-4-1kxbamy_html_a7092cc888cf8795.png)

After taking a look at how you can use Wireshark to extract some pieces of information, let&#39;s analyze a malicious traffic. As a demonstration we are going to analyze this [pcap](https://www.malware-traffic-analysis.net/2019/12/03/2019-12-03-traffic-analysis-exercise.pcap.zip) from the same source (the password is &quot;infected&quot;). Some additional alerts file can be found [here](https://www.malware-traffic-analysis.net/2019/12/03/2019-12-03-traffic-analysis-exercise-alerts.zip).

Open the pcap file with Wireshark. We are going to find:

- The IP address, MAC address, and host name of the infected Windows host
- The Windows user account name of the victim
- The used Malware

![](RackMultipart20200926-4-1kxbamy_html_d85d81df118c207a.png)

By highlighting &quot;Internet Protocol Version 4&quot; we can get the IP address which is:  **10.18.20.97**

![](RackMultipart20200926-4-1kxbamy_html_6b4017eeba993024.png)

The MAC address is:  **00:01:24:56:9b:cf**

![](RackMultipart20200926-4-1kxbamy_html_ac76cd9d78ba026a.png)

Like what we did previously to detect the hostname we can see that the hostname is: JUANITA-WORK-PC

![](RackMultipart20200926-4-1kxbamy_html_2a39e608d0e61bc3.png)

To get the windows user account by analyzing the kerberos traffic using this filter:  _ **kerberos.CNameString** _

![](RackMultipart20200926-4-1kxbamy_html_8064544e08c96738.png)

The Windows account name is:  **momia.juanita**

Based on the alerts we can get that the malware was a variant of &quot; **Ursnif**&quot;

![](RackMultipart20200926-4-1kxbamy_html_ed3361251e2756cf.jpg)

_ **Ursnif** __ __ steals __ system information and attempts to __ steal __ __ banking__ and online account credentials. (from: F-Secure __Labs__: _[_https://www.f-secure.com/v-descs/trojan\_w32\_ursnif.shtml_](https://www.f-secure.com/v-descs/trojan_w32_ursnif.shtml)_ )_

The malware appears to come from a mail because if you notice closely you will find that the victim visited mail.aol.com:

![](RackMultipart20200926-4-1kxbamy_html_7c0560c43e68b496.png)

I hope you found it helpful.

**Summary**

In this article, we explored Wireshark and how to use to perform malicious traffic analysis.

To learn more about traffic analysis you can download this doc that contains many useful resources: [Malicious Traffic Analysis Resources ](https://static.peerlyst.com/image/upload/v1584025330/post-attachments/Malicious_Traffic_Analysis_Resources_s8ijhc)

**References and Credit**

- [https://www.peerlyst.com/posts/how-to-exploit-and-secure-routers-chiheb-chebbi?trk=search\_page\_search\_result](https://www.peerlyst.com/posts/how-to-exploit-and-secure-routers-chiheb-chebbi?trk=search_page_search_result)
- [https://unit42.paloaltonetworks.com/using-wireshark-identifying-hosts-and-users/](https://unit42.paloaltonetworks.com/using-wireshark-identifying-hosts-and-users/)
- [https://www.malware-traffic-analysis.net/2019/12/03/index.html](https://www.malware-traffic-analysis.net/2019/12/03/index.html)
