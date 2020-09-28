## Hands-on Malicious Traffic Analysis with Wireshark


Communication and networking are vital for every modern organization. Making sure that all the networks of the organization are secure is a key mission.In this article we are going to learn how to analyze malicious traffic using the powerful tool Wireshark.

![](https://lh5.googleusercontent.com/UrICols41RopVGU5ivRDDegsuk8n3EFj1LxIwWIkNlP2IlJUllcO9llKaj48KsqCkUyFZOFAUsNiZePIR9f83T9Rfsl1jdfgZH0s18ebxsAmJ6xBq19-smjtkzChXy2llHHzZfo)

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

## Network Topologies 

A topology is a schematic representation of a network. You can see it as the layout of the network and how the connected devices are arranged in the network. In networking we have many topologies some of the them are:

- **Ring Topology: ** the data flows in one direction
- **Star Topology: ** all the devices are connected to a single node (Hub)
- **Tree Topology:** this topology is hierarchical
- **Bus Topology: ** all the devices are connected to a central connection
- **Fully-connected Topology:**  each device is connected with all the other devices of the network

## **What is a network traffic?**

[Techopedia](https://www.techopedia.com/definition/29917/network-traffic) defines it as follows:

> &quot;_Network traffic refers to the amount of data moving across a network at a given point of time.  __Network data__  is mostly encapsulated in  __network packets__ , which provide the load in the network.  __Network traffic__  is the main component for network traffic measurement, network traffic  __control__  and simulation.&quot;_

<img src="https://lh5.googleusercontent.com/vwga5qw-V31q2A0kUEHQ-sEVqKqCzsLI4ToCNuP65bVjFq4wmBQRlkTVmm6hhsWURsO9Gpj31SyS-eZMc1n9AXjme7CyNIkHyOVBXoqM0P1JSmJSzWwt9Ol7kyFFZawiLhxtMeI" width="200px">


[Image Courtesy](https://www.flowmon.com/getattachment/Solutions/use-case/flow-monitoring/product-img_Monitoring.png.aspx?width=480&amp;height=309)

## **Traffic Analysis with Wireshark **

<img src="https://lh3.googleusercontent.com/24OiDT6gcn37TKewMOJAb_JJjZYmng44HidSs60bQOA3LZPwX4ZfaelU9QRQkFIXCBFsECeQyCTvoME9VaVek98kKPFONTESHEznLcgAtlyIUYJDCJjXeCjqF0SP73pmU7DzGjU" width="200px">


The most suitable tool that will help you analyze your network traffic is definitely Wireshark. Wireshark is a free and open-source tool to help you analyse network protocols with deep inspection capabilities. It gives you the ability to perform live packet capturing or offline analysis. It supports many operating systems including Windows, Linux, MacOS, FreeBSD and many more systems.

You can download it from here: [https://www.wireshark.org/download.html](https://www.wireshark.org/download.html)



![](https://lh6.googleusercontent.com/HKb3zNrtDk8dOr8N7guWe3tfPC2cv4StzdlWJX_hEGUiEE9DjP3G_rVYxWZAzdtB7ZG8Co90x9xXIfZrSmufeGjBnf0AMjqBo2PrUuEye27MKYWNyvvqGDToDaYfX5E_d3osdXc)

Wireshark will help capture and analyze traffic as  **pcap**  files. The analysis follows the OSCAR methodology:

- Obtain
- Strategize
- Collect Evidence
- Analyze
- Report

![](https://lh3.googleusercontent.com/7sOHkaMZjyh022rylu0xSLl3uoiPLzqOqk5Tqa6sqv4Mj-YQpCrrTDPCdUGVS9MDGkQU6Tup-GvSrh04iAF5M7rH2Ee8bB_ppPgEb4xzn_35p6FthAtiEVazeLaTSoD613yvsV8)

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

<img src="https://lh4.googleusercontent.com/VL-XEpcWKBcUh7y4JqGFXI_r560HFpAzuAcm5cALemlmCHE7Jt8fXCBs_JZ0REVzZCdm4py6YQxd9_PD8jioMA87a81qwcuQB2yS4ifcCOVTkJ3X_zrRi03HZQ3RynvZ7QCwuc8" width="400px">


[Image Courtesy](https://www.researchgate.net/profile/Jay_Johnson3/publication/322568288/figure/fig6/AS:631584889778238@1527592980914/OSI-model-seven-layer-protocol-stack-28.png)

As a first demonstration let&#39;s start analyze a small [pcap](https://www.malware-traffic-analysis.net/training/host-and-user-ID-pcap-01.pcap.zip) delivered by _malware-traffic-analysis.net. _The file password is &quot;_infected_&quot;

Once you open it with Wireshark you will get this main window:

![](https://lh3.googleusercontent.com/UEjDUjkN9DXhmataeTjAeL4mW4cVh7j_AbPVcDvkZRuYl9WJz6AWKB2hfAWo0PoQdk8jwYYmPHcpChxdXGfhgW8walSf-PLvFN1TahQrHbZHRWz4IzaO9-KYH6YQ2z63Sxpla90)

Let&#39;s start collecting some helpful information like the Host, destination, source etc...

To get the host we can use the DHCP filter.

Dynamic Host Configuration Protocol (DHCP) is a network layer protocol based on RFC 2131 that enables assigning  IP addresses dynamically to hosts. It goes through 4 steps:

- _Discovery _
- _Offer_
- _Request_
- _Acknowledgment_

![](https://lh4.googleusercontent.com/HiynnOar7p6WWpYNNpTbK3B1JuuAiE_GimUiKULLMiJU1hqVrmtW9k5dPRRmXFD4N9D7B5qCQRWKCnuua9c97B0swwq5juTa_5zb2RRJlrXT1zjCE9jaR1KnyDalM99YvmdRe5o)

To learn more about Filters check this great resource:_ _[Using Wireshark – Display Filter Expressions](https://unit42.paloaltonetworks.com/using-wireshark-display-filter-expressions/)

Now select: DHCP Request and you will get many helpful pieces of information including the client Mac address. In switching the traffic of data is determined by Media Access Control (MAC) addresses. A MAC address is a unique 48-bit serial number. It is composed equally of the Organizational Unique Identifier (OUI) and the vendor-assigned address.MAC addresses are stored in a fixed size table called the Content Addressable Memory (CAM)

![](https://lh6.googleusercontent.com/NhVDWhVps0TpxzTGCK6c5NxIynjSSyIH5uaIttU2FfDA_VZXpjDuzFSIoCihiQcjuH9RIluRXnxGgatQ-Xyg4OXenZcEG-r2qZgS9-dulGfdrC68Cy1IaCBAicEXgWi-KZI0zac) 

And you will get also the hostname. It is &quot;_Rogers-iPad_&quot;

![](https://lh4.googleusercontent.com/cvPYnSmQPbkyoMiMML4T_2CgFeHdzs3Lnvjps2YN1_JUAGEW2ZT5GK0ge4UdpiPYdO4ujPmu0Rjdv76ce5ncsGn9Gq_hmUwjkb0rfEv19PqQvkFSlZbLrx7VqjnJ_-jinHK4dwQ)

After taking a look at how you can use Wireshark to extract some pieces of information, let&#39;s analyze a malicious traffic. As a demonstration we are going to analyze this [pcap](https://www.malware-traffic-analysis.net/2019/12/03/2019-12-03-traffic-analysis-exercise.pcap.zip) from the same source (the password is &quot;infected&quot;). Some additional alerts file can be found [here](https://www.malware-traffic-analysis.net/2019/12/03/2019-12-03-traffic-analysis-exercise-alerts.zip).

Open the pcap file with Wireshark. We are going to find:

- The IP address, MAC address, and host name of the infected Windows host
- The Windows user account name of the victim
- The used Malware

![](https://lh4.googleusercontent.com/3zbB_a_cYmJxJcNlGhrrttlaMOR3Hh-RzqqKQJ4KmxLei2pc6aoxyXhZUtoWEPEqhPAUcQ3V3K1qB1_AaFxlZLzWCOiq-djWrQjgKV-Xg6cJgxTGACxrHtXLwF_iQjA_Al4vuIE)

By highlighting &quot;Internet Protocol Version 4&quot; we can get the IP address which is:  **10.18.20.97**

![](https://lh6.googleusercontent.com/gjMBtHa2nFrPS2KeGlI6uSYSGwHpJ-XH2jGN771hPyR3gVDWJUj7r6hcC2WLPswc4kEyEydagbDcJG7N-kon1Ntk3ppk3kzI1ZHsgiRmP27SxDlq7fz9_Qz-EQD9vTzKP7XMYy8)

The MAC address is:  **00:01:24:56:9b:cf**

![](https://lh6.googleusercontent.com/mBZrNN8ToZuXkiDpzhOn_tRgeKIbmA-S5_REw6er9fp67RSe3Xwup0K77ns87k6ekt1GZqI-uDq2DckhCie7yiYCsokC_3jSlACC4bYWjz2k4PHN-Tcm1MDacaYxnyju2zDVCDw)

Like what we did previously to detect the hostname we can see that the hostname is: JUANITA-WORK-PC

![](https://lh3.googleusercontent.com/hyxXXUwucYsQBjzeU-Z5lNJgeQKezZBotd6yUqhc_ey_zZNTNLzCwOArYffgMl-UEvSCoKQKnu_aleAg_i-I940fyjwlIiqIFNyGM2JNzNdSkQJfAswbB7slwJzf9ZpG8LBXrXU)

To get the windows user account by analyzing the kerberos traffic using this filter:  _ **kerberos.CNameString** _

![](https://lh6.googleusercontent.com/TfIAZWFOnC7uUgDCpwnZulxOQPKz_j1_XbAG9RXIWj7Id-CphfRCG1ebXJtSlClSC13uIvAeIQVUTy2JEFqQ90vr8LSxz-vh0C0UR_PhPS8I4ZM73nTrwlm5oN63UHa74UV-eiY)

The Windows account name is:  **momia.juanita**

Based on the alerts we can get that the malware was a variant of &quot; **Ursnif**&quot;

![](https://lh5.googleusercontent.com/9UKbU1ILuJsdtS3dPGLj_HTGgjc2lmYOIZf-C9JbKa2VnZJEji439gZx7gFrhYzAh53JK2MBRV7tMf6G4xM96i76eBG_3IAShkwaXL-SfoqjhKTB-kNTdzB40wKuCi6VzT_AYCw)

_ **Ursnif** __ __ steals __ system information and attempts to __ steal __ __ banking__ and online account credentials. (from: F-Secure __Labs__: _[_https://www.f-secure.com/v-descs/trojan\_w32\_ursnif.shtml_](https://www.f-secure.com/v-descs/trojan_w32_ursnif.shtml)_ )_

The malware appears to come from a mail because if you notice closely you will find that the victim visited mail.aol.com:

![](https://lh5.googleusercontent.com/PB-ArIM5z8QKB-Wop72a6FauzVam1MRjyyeUSMb7zH4gAtuF17jjbkDd_erqJ02_jhVWCdbr3JRM4J66JhdBY0n0S0f6a5eNjBc3e5KxpX9FMUm4F4rohRq8z1xjbZtORrPkhGA)

I hope you found it helpful.

**Summary**

In this article, we explored Wireshark and how to use to perform malicious traffic analysis.

To learn more about traffic analysis you can download this doc that contains many useful resources: [Malicious Traffic Analysis Resources ](https://static.peerlyst.com/image/upload/v1584025330/post-attachments/Malicious_Traffic_Analysis_Resources_s8ijhc)

**References and Credit**

- [https://unit42.paloaltonetworks.com/using-wireshark-identifying-hosts-and-users/](https://unit42.paloaltonetworks.com/using-wireshark-identifying-hosts-and-users/)
- [https://www.malware-traffic-analysis.net/2019/12/03/index.html](https://www.malware-traffic-analysis.net/2019/12/03/index.html)

