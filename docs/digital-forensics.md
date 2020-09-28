# Hands-on Guide to Digital Forensics


Digital forensics is one of the most interesting fields in information security. In this post, we will explore what digital forensics is and we will learn how to perform some digital forensics tasks using some powerful tools and utilities.

![](https://lifars.com/wp-content/uploads/2018/12/Digital-Forensic-Art-720x480.jpg)


In this article we are going to explore the following points:

- **Digital Forensics Fundamentals**
- **Digital Forensics Lab**
- **Network evidence collection and Analysis**
- **Host-based evidence collection and Analysis**
- **Forensics Imaging**
- **Practical Lab: Autopsy Forensics Browser**
- **Practical Lab: Memory Analysis with Volatility**


## **Digital Forensics Fundamentals**

Before diving into the practical labs it is essential to explain many important terminologies. First, _what is digital forensics_?

NIST is describing Forensics as the following:

> _The most common goal of performing forensics is to gain a better understanding of an event of interest by finding and analyzing the facts related to that event... Forensics may be needed in many different situations, such as evidence collection for legal proceedings and internal disciplinary actions, and handling of malware incidents and unusual operational problems. _

Like any methodological operation, Computer forensic analysis goes through well-defined steps:  **Identification** ,  **Preservation** ,  **Collection** ,  **Examination** ,  **Analysis**  and  **Presentation**.

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/012216_2245_DigitalFore2.png)

[Figure](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/012216_2245_DigitalFore2.png)

let&#39;s explore these steps one by one:

- Identification
- Preservation
- Collection
- Examination
- Analysis
- Presentation

According to [worldsecuresystems](https://computer-forensics.worldsecuresystems.com/what-is-a-chain-of-custody.html):

> &quot;A chain of custody is a document that is borrowed from law enforcement that tracks evidence from the time the Computer Forensics Examiner gains possession of the item until it is released back to the owner. &quot;

The following illustration presents a chain of custody template:

![](https://www.joshmoulin.com/wp-content/uploads/2015/05/Screen-Shot-2015-05-11-at-1.48.29-PM.png)

[Figure]()

## **Digital Forensics Lab  **

To perform digital forensics, obviously, you need to prepare a lab for it. It is essential to have both the required hardware and software.

### **Hardware **

During investigations, digital forensics experts are dealing with many hardware pieces and devices including RAMs and Storagemedia devices. Thus, it is important to acquire a suitable hardware equipment to perform the task in good condition. Some of the required hardware pieces are the following:

- A digital Forensics laptop (A minimum of 32 GB of RAM is recommended) with an OS that contains the needed digital forensics tools
- A secondary machine with Internet connexion
- A physical write blocker

![](https://upload.wikimedia.org/wikipedia/commons/8/8e/Portable_forensic_tableau.JPG)[Figure](https://upload.wikimedia.org/wikipedia/commons/8/8e/Portable_forensic_tableau.JPG)

### **Software**

As I said previously, a digital forensics computer needs to be equipped with many DF tools. Some of the most used tools and operating systems are the following:

- _SANS SIFT_
- _CAINE OS_
- _Volatility _
- _X-Ways Forensics_
- _Autopsy: the Sleuth Kit_
- _Bulk Extractor_

![](http://linoxide.com/wp-content/uploads/2016/07/CAINE.jpg)

[Figure](http://linoxide.com/wp-content/uploads/2016/07/CAINE.jpg)

## **Network evidence collection and Analysis **

An evidence is the information to be investigated. Digital forensics analysts are dealing with different categories of evidence including  **network-based evidence**  and  **host-based evidence**. Let&#39;s start exploring how to deal with network evidence. As we cited earlier, the first step is collecting the evidence. In networking, we can perform the collection using many techniques and tools. After identifying the source of evidence using for example network diagrams, you can use packet capture tools such as:

### **TCPdump **

![](https://lh6.googleusercontent.com/CBxVE9DD2GEj9OzqWMkXWRB4H1BUdex__WIJNvSCUjNDQl4Zu1AuTurOe_kEkeCUxrcKdQtJmPTl2GfRrK1Obj4cn4E84fGQuHZ1_Lljs2rGYEl5HBTmUULSb5J6QGlr7Nb506I)

&quot;_Tcpdump is a powerful command-line packet analyzer; and  __libpcap__ , a portable C/C++ library for  __network traffic__  capture.&quot; (Source: tcpdump.org)_

### **Wireshark **

![](https://lh3.googleusercontent.com/EhUPNsUQeUqnPVxCgaRQ7LXu3Xb1zWQo-cdn2jMsn3QcfgLj2RvGH1KuD7syif-C8TC56G5BVxBhHEa2UnBntQAGf1kgxjGL_rLI_L326ZvZ_q8AUjWRIDlc1SlDBP3ckX5fsW8)

> &quot;_Wireshark is the world&#39;s foremost and widely-used  __network protocol__  analyzer. It lets you see what&#39;s happening on your network at a microscopic level and is the de facto (and often de jure)  __standard__  across many commercial and non-profit  __enterprises__ ,  __government agencies__ , and educational institutions.  __Wireshark__   __development__  thrives thanks to the  __volunteer__  contributions of networking  __experts__  around the globe and is a continuation of a  __project__  started by Gerald Combs in 1998&quot;.  (Source:  __**wireshark.org**__ )_

As a demonstration let&#39;s explore how to analyse a small  **pcap**  file with Wireshark.

If you are using Kali Linux, Wireshark is already installed there.

Open Wireshark

![](https://lh6.googleusercontent.com/4SMBP8FlcLL9Jc3YpcfNJrH1GU-Jd9wUbHqpKwNecEe-kRXu9va3uajaUvURgJ_jWmTC-M9UEcyii7P0Wu-r7ZwQHUnbIlaxwN1IqrKzdcJMDUdKvHd4INUsznHMy1VE4gn-Eyc)

We are going to analyse this Pcap file [http\_with\_jpegs.cap.gz](https://wiki.wireshark.org/SampleCaptures?action=AttachFile&amp;do=get&amp;target=http_with_jpegs.cap.gz) from here: [https://wiki.wireshark.org/SampleCaptures](https://wiki.wireshark.org/SampleCaptures)

Open the file with Wireshark:

![](https://lh3.googleusercontent.com/TrhRkkdztntNWCViPUCi-tJJfIfYXlDHMSha_YGcNR-eA3tscNQLhrWAjmI42MyKp-4v6qO3IJbNhbkLCuTRzPodZ6uX5fNLAmVfK0BC-iT1IXnf8V4WXZw17Od4UJGdIhuA-eY)

To select a TCP stream go to  **Analyze**  -\&gt;  **follow TCP stream**

![](https://lh3.googleusercontent.com/ejE_cFyNt6aXXBpeOuaNgDT06O1etKtNZkqfJonbZM9Xy6ZAfKui7gKQVoEUDsskDCn9P9Qg-OmvC0_4HPIojHR9noOfdq99I9uNQdnAWJqcbv7iTFHbvCUIfOfutrwBi1JdWtU)

For example, we are going to extract the files from the captured packet:

Go to  **File**  -\&gt;  **Export objects**  -\&gt;  **HTTP**  -\&gt;  ** Save all**

![](https://lh5.googleusercontent.com/dlnI7uFm67IHSc4nMwWMGDmH_QahIXMht2CLHA_NoQkzvw_QFEHxhd59nbHVdbEOZqploY7mg0MyybxVa-qO2iOMON7YtUVSp6toaVLmiIXoXFx7vznXo44N_qlIvDC3LM4_Dmw)

Voila! we extracted the included files:

![](https://lh6.googleusercontent.com/XSu_aqBFCzSfiZKjm_v8HqTOBKUTGdm9R-jzxtYM3OuhQhnQ1YFCOCaJrsNavHFs6ZqeFUccsNjRDRsFiYhiKjdord4X7m2tiPV_6_h3tXOesc_PVSgg14L6gESOhbwgg2bi0UU)

## **Host-based evidence collection and Analysis **

As an investigator and digital forensics expert, it is essential to acquire knowledge about the different storage means and the different filesystems. By definition, a storage media is a device where we can store data and information. There are many used storage devices including:

- _Hard drive_
- _DVD-ROM_
- _USB drive_
- _Memory cards and so on _

![](http://vskills.in/certification/blog/wp-content/uploads/2016/01/storage-devices.jpg)

[Figure](http://vskills.in/certification/blog/wp-content/uploads/2016/01/storage-devices.jpg)

The removable storage media pieces need to be formatted with a specific filesystem. Some of the most used filesystems are:

- _Ext4_
- _Ext3_
- _NTFS_
- _FAT32_

To collect host-based evidence, you need to know the difference between volatile data and non-volatile data. Volatile data is data that is lost after a shutdown or some system changes. CPU data and ARP cache are some forms of volatile data. Data stored in hard drives and Master File Table (MFT) entries are non-volatile data. The host-based evidence acquisition can be done locally or remotely. Also, it can be done online or offline. Evidence collection is performed with what we call &quot;Forensics Imaging&quot;

## **Forensics Imaging **

Forensics imaging is a very important task in digital forensics. Imaging is copying the data carefully with ensuring its integrity and without leaving out a file because it is very critical to protect the evidence and make sure that it is properly handled. That is why there is a difference between normal file copying and imaging. Imaging is capturing the entire drive. When imaging the drive, the analyst image the entire physical volume including the  **master boot record**. There are two imaging techniques:

- Live imaging: the compromised system is not-offline
- Dead imaging: the compromised system is offline

Also, the taken images can be in many formats such as:

- Raw images
- EnCase evidence files
- AFF
- Smart and so on

For imaging, you can use [FTK Imager](https://accessdata.com/product-download/ftk-imager-version-4-2-0):

&quot;_FTK Imager is a data preview and imaging  __tool__  used to acquire data (evidence) in a  __forensically__  sound manner by creating copies of data without making changes to the original evidence.&quot;_

![](https://techtalk.gfi.com/wp-content/uploads/2016/02/FTK_Imager.png)

[Figure](https://techtalk.gfi.com/wp-content/uploads/2016/02/FTK_Imager.png)

## **Practical Lab 1: Autopsy Forensics Browser **

As a second demonstration, we are going to learn how to use a great forensics tool called &quot;Autopsy Forensics Browser&quot;. According to [https://www.linuxlinks.com/autopsy/](https://www.linuxlinks.com/autopsy/) :

> _The Autopsy  __Forensic__   __Browser__  is a graphical  __interface__  to the  __command line__  digital  __investigation__  tools in The Sleuth Kit. The two together enable  __users__  to investigate volumes and file  __systems__  including  __NTFS__ ,  __FAT__ , UFS1/2, and Ext2/3 in a &#39;File Manager&#39; style interface and perform  __key__   __word__  searches._

If you are using Kali Linux, can found it directly there without the need to install it:

Run it from the menu:

![](https://lh4.googleusercontent.com/HRg3MbMv7anzrFFeA7v_0tkweKkQP-y3WtX1ZGgkRn1qZZ_AoemxSApKZV1dZQIZRDxI6siGbdRZlYvlsAyVNKfuw4ynCszBzOyEq4Mon5W3bE9zirNfdpoLlby5XyZFxxJOQLI)

Go to:

`http://localhost:9999/autopsy`

![](https://lh6.googleusercontent.com/JUyVnThH56Y9_OgESxi9TXJLaQtNjsf_Up3o6bar41Ar_xsniDDRrAKbpx6juY7dIRmCDDa5NGW2qT_Ac5-tPWob2qnfvRxw-JZ5CGZDuRbCU1wgQV8NCRloHRTt7A8VxYd1Jzw)

Create a new case:

![](https://lh3.googleusercontent.com/RrtbKuF1CU_l88mg6AQbJ0OZCNkQ0Xa9JJG7N2WD23Riov_tk_59cF-lbMqmFzGjr_QcKTJIujLiLJii0MYlHL-91MjnUEnTr17-yfjjqmt9DYIO8yyTmLASs2v7QVe3qVeEMfk)

Select the profile

![](https://lh4.googleusercontent.com/cYulRe2tRbIyhk5qIdh8aFtG-Y1ie09dyWC8APtuupGWBvA3OygMrA4i7gl8--ZQ-6P1P1X8RrGCvWfh4QeppCH4Sg5iag6YD2pg6_-Z98K0wGyQmA1pY1eGDLcr8-tKWtv43nw)

Add a host

![](https://lh3.googleusercontent.com/_PUjLqGarRV0ecHLlnilMNN5UzIGXILznMUlVR-2C0LwEluy2NpwIHz4UgpU1FTiQfIuz0ooeITyGy3_KlepPbxe4-DwPSQwd_KkS-4nYtoTgvLiIcJe9oPuzaIPPc1EUXLCqKI)

Check the configuration and click Add Image

![](https://lh4.googleusercontent.com/1k-qltQ3ypyaJf0ipKkl-PIRHfofkJNWaUaRbAr4Zk88o37jmMel1REI9ZiMWXf-kMvOf3nK7-JmmyLMV2PjiLI97BSX82U5vZJeDxhlNJAN8QuNTGk8BxG1g7jtYYQoyngXXbE)

For the demo, we are going to use a memory dump sample (NTFS Undelete) from  [http://dftt.sourceforge.net](http://dftt.sourceforge.net/) (Digital Forensics Tool Testing Images)

![](https://lh4.googleusercontent.com/hBk_dFWG6almtmnavdD2X-vOESdf1xqrbly7knkx5HjVNgkSyFVcJN2Pl79Jc5EBYXbx-5GWRfEVhfyrlfX-YPRnidIXrZm02ZFmX1FE64AuGM1bswIC3hOCGGGentcUTAb9M7E)

Add the path of the dump:

![](https://lh5.googleusercontent.com/eTIBkM4YlCy4vayFfKriI_XkThl0sLAZSM27WuBw6-Vt0ch4hWvcClubB34Y3oMLwaVThL6rLtU51lkRknUoCBGBtla_YMiuJeqJ2n69s7dt5tISix2tnoKsxIfDZ6Fhe1yRtvQ)

Click on Analyze:

![](https://lh3.googleusercontent.com/VK7CRCv004FH8qMZ1-3JUw78pfA3c3sBjsXO151tkUUUnGrj6foGe3pAxcFQ-z9j32waZ2E9_Syno_4PicKYdWkonx2fuK124apm1Mlgf8eqVSrmYfK_m0KgEOGMRYb64RNkKFI)

These are some pieces of information about the dump

![](https://lh6.googleusercontent.com/Fd861fON2uR-l6V4g7D61ZVb479Xtm6vZcxbCBcpradTOoz852eVc_Ytcj3e7_Q1W-Pnk9FDG6WZDbgSfBhvYeG2qoG0eLnX8bDjkPl4sLdFFvQTX3X9Ql70l3tI1u4acuKs-d0)

Now you can analyse the file freely:

![](https://lh4.googleusercontent.com/N_XZqgiCR3VAm-bsqejK-5jGAJweVXwpp8E1-ai3Atrq96OqQRH2JrgMp2G9O5RBAVmxkM7N1jjs0RjaHPviLxQ0rNX5szOpbcPljbbXYvIxLYiBMyTtQR9YEYjHn3wuNmM0XkQ)

## **Practical Lab 2: Memory Analysis with Volatility **

Memory malware analysis is widely used for digital investigation and malware analysis. It refers to the act of analysing a dumped memory image from a targeted machine after executing the malware to obtain multiple numbers of artefacts including network information, running processes, API hooks, kernel loaded modules, Bash history, etc. ... This phase is very important because it is always a good idea to have a clearer understanding of malware capabilities.

- Process list and the associated threads
- Networking information and interfaces (TCP/UDP)
- Kernel modules including the hidden modules
- Opened files in the kernel
- Bash and commands history
- System Calls
- Kernel hooks

To analyse memory You can simply use volatility framework, which is an open-source memory forensics tool written in Python. It is available under GPL. Volatility comes with various plugins and a number of profiles to ease obtaining basic forensic information about memory image files. To download it you can visit this website: [The Volatility Foundation - Open Source Memory Forensics](https://www.volatilityfoundation.org/) or [GitHub - volatilityfoundation/volatility](https://github.com/volatilityfoundation/volatility)

As a hands-on practice, we are going to analyse a memory dump from an infected computer with Volatility. You can find many samples here:  [https://github.com/volatilityfoundation/volatility/wiki/Memory-Samples](https://github.com/volatilityfoundation/volatility/wiki/Memory-Samples)

For the demonstration, we are going to analyse a memory dump called &quot; **cridex.vmem**&quot;

`wget http://files.sempersecurus.org/dumps/cridex_memdump.zip`

Get info about the memory dump:

`python vol.py -f cridex.vmem imageinfo `

![](https://lh6.googleusercontent.com/qhHh7VGDwEc9Kw64HCTecEXfXucBQaiBNWqZIBiwRJqTWTejXpIw2N2tdlhyjC1yVPPsoQVF-iGZ76zauqvjxk6spDVDl2Lq1YfSKCps1WmSOt5Ek7RehrkC69oAy08vazrHEsQ)

Get Processes

`python vol.py -f cridex.vmem psxview`

![](https://lh6.googleusercontent.com/RycgECH3b-ET-QcfQxTIMbw2Jze6p_mHMpc84xkpHhd83TYqxdqB-gcAvm757YriFzCw0ThjnNiP1epoifBDo1LUIrsGb1RNUepvJU8jCqPmoFnL2hWCGnvlbIFmtxw6yqVTM1c)

Processes as Parent/Child

`sudo python vol.py -f cridex.vmem pstree`

![](https://lh5.googleusercontent.com/Ldy0BJfoY4CxQ8l058uxFYswOaN5IKbxzOFnYTOKRW-Rwl3flfD5_y5E0u0ZjLRuBsRDp1Vvw-9VKtqKkqR5-a4eytxHV8-C-WgfAhLyxzOFst1KotGkRboOnQRBGe48wXgkF5g)

Get hidden and terminated Processes

`sudo python vol.py -f cridex.vmem psscan`

![](https://lh5.googleusercontent.com/Ldy0BJfoY4CxQ8l058uxFYswOaN5IKbxzOFnYTOKRW-Rwl3flfD5_y5E0u0ZjLRuBsRDp1Vvw-9VKtqKkqR5-a4eytxHV8-C-WgfAhLyxzOFst1KotGkRboOnQRBGe48wXgkF5g)

Get DLLs

`sudo python vol.py -f cridex.vmem dlllist`

![](https://lh5.googleusercontent.com/C1e-XZqhkpeWgBMEhyvQazrddYah9W42hP6yiZTfjquyDKIASHZQ3oxCVUf7auXUJDfAFRr0jNtlg3WILnEGUgC1SlxbTdwYLHF4YibvJ-MHWueHRLpZ6LQmyyzBX6o5cC11tgU)

Get commandline args

sudo python vol.py -f cridex.vmem cmdline

![](https://lh4.googleusercontent.com/wG_xkO-k2sVXzEmo27rBLCdPjKQeJdQ3Mkzcv0K26_1nnOpakQNqeBy2NaAFo6ID095K2qL2OKXjACWJpaWF6-IeFV3FJLS_NTKGJei0vmScJtol4Urk97g2dgkWURGRV_UPEIk)

Get SIDs:

`sudo python vol.py -f cridex.vmem getsids`

![](https://lh5.googleusercontent.com/hbJIE7yFugDB7a9FI-MA5O1T2aiCcSwbFrh-WBlhNmPhmC-z-LSiiKrW8ansREkcGv__-XYOOsxgPeoeIcOIE_485P-AigdSSG7pkv60wj3UbJFOB1jpKl4pNE_ClWgJ_9Zuvmc)

Networking information:

`sudo python vol.py -f cridex.vmem connscan`

![](https://lh6.googleusercontent.com/keXXK0MmYfkSUFUobN4SkUHbmHVO30j85lo4wIhZQbxFz535zXySsW6QpHVLsSB0otCXEYu4L-xCnIfLt2-Zuz5DbDcejvlE694FUAOk4tMhdSb0ufPdB6KZ5tft8RyThQZWmvo)

Kernel modules:

`sudo python vol.py -f cridex.vmem modules`

![](https://lh5.googleusercontent.com/GpAix9_AiI4dfp4WiUZMmh8FvqR4igg10bA2u4JIIy1UBSMOMHMUf-10dLTz2DlM9U5uo1NAfhOTu2YZbnypNu6MNZQbTZFqfmWdL6zV7Dmnbr5CI5MAA__kuVHAr8Euxu49CHU)

For more information about the most used Volatility commands check these two helpful cheatsheets:

- [Volatility foundation CheatSheet\_v2.4.pdf](https://downloads.volatilityfoundation.org/releases/2.4/CheatSheet_v2.4.pdf)
- [SANS Volatility-memory-forensics-cheat-sheet.pdf](https://digital-forensics.sans.org/media/volatility-memory-forensics-cheat-sheet.pdf)


## **References:** 

- [https://wiki.wireshark.org/SampleCaptures](https://wiki.wireshark.org/SampleCaptures)
- [Digital Forensics and Incident Response](https://www.packtpub.com/networking-and-servers/digital-forensics-and-incident-response)
- [Digital Forensics with Kali Linux](https://www.packtpub.com/networking-and-servers/digital-forensics-kali-linux-0)

## **Summary**

In this module, we discovered what digital forensics is, what are the different steps to perform it, including evidence acquisition and analysis. Later, we explored some well-known digital forensics tools by analyzing some memory dumps using Autopsy and Volatility framework.


