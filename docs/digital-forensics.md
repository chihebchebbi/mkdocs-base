Hands-on Guide to Digital Forensics

  **Introduction  **

Hi Peerlysters,

Digital forensics is one of the most interesting fields in information security. In this post, we will explore what digital forensics is and we will learn how to perform some digital forensics tasks using some powerful tools and utilities.

![](RackMultipart20200926-4-4zxqee_html_6c6f274fbd9d1ae1.jpg)

[Figure](https://lifars.com/wp-content/uploads/2018/12/Digital-Forensic-Art-720x480.jpg)

In this article we are going to explore the following points:

- **Digital Forensics Fundamentals**
- **Digital Forensics Lab**
- **Network evidence collection and Analysis**
- **Host-based evidence collection and Analysis**
- **Forensics Imaging**
- **Practical Lab: Autopsy Forensics Browser**
- **Practical Lab: Memory Analysis with Volatility **

To get the most from this article, you can download this helpful document that contains more resources about Digital Forensics: [Digital Forensics Resources](https://static.peerlyst.com/image/upload/v1574535872/post-attachments/Digital_Forensics_Resources_fbxea2)

**Digital Forensics Fundamentals**

Before diving into the practical labs it is essential to explain many important terminologies. First, _what is digital forensics_?

NIST is describing Forensics as the following:

_The most common goal of performing forensics is to gain a better understanding of an event of interest by finding and analyzing the facts related to that event... Forensics may be needed in many different situations, such as evidence collection for legal proceedings and internal disciplinary actions, and handling of malware incidents and unusual operational problems. _

Like any methodological operation, Computer forensic analysis goes through well-defined steps:  **Identification** ,  **Preservation** ,  **Collection** ,  **Examination** ,  **Analysis**  and  **Presentation**.

![](RackMultipart20200926-4-4zxqee_html_f02d2e6db0f5a7df.png)

[Figure](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/012216_2245_DigitalFore2.png)

let&#39;s explore these steps one by one:

- Identification
- Preservation
- Collection
- Examination
- Analysis
- Presentation

According to [worldsecuresystems](https://computer-forensics.worldsecuresystems.com/what-is-a-chain-of-custody.html):

&quot;A chain of custody is a document that is borrowed from law enforcement that tracks evidence from the time the Computer Forensics Examiner gains possession of the item until it is released back to the owner. &quot;

The following illustration presents a chain of custody template:

![](RackMultipart20200926-4-4zxqee_html_80ca4b3c8c751cf8.png)

[Figure](https://www.joshmoulin.com/wp-content/uploads/2015/05/Screen-Shot-2015-05-11-at-1.48.29-PM.png)

**Digital Forensics Lab  **

To perform digital forensics, obviously, you need to prepare a lab for it. It is essential to have both the required hardware and software.

**Hardware **

During investigations, digital forensics experts are dealing with many hardware pieces and devices including RAMs and Storagemedia devices. Thus, it is important to acquire a suitable hardware equipment to perform the task in good condition. Some of the required hardware pieces are the following:

- A digital Forensics laptop (A minimum of 32 GB of RAM is recommended) with an OS that contains the needed digital forensics tools
- A secondary machine with Internet connexion
- A physical write blocker

![](RackMultipart20200926-4-4zxqee_html_a29d8c2ecf895ed9.jpg)[Figure](https://upload.wikimedia.org/wikipedia/commons/8/8e/Portable_forensic_tableau.JPG)

**Software**

As I said previously, a digital forensics computer needs to be equipped with many DF tools. Some of the most used tools and operating systems are the following:

- _SANS SIFT_
- _CAINE OS_
- _Volatility _
- _X-Ways Forensics_
- _Autopsy: the Sleuth Kit_
- _Bulk Extractor_

![](RackMultipart20200926-4-4zxqee_html_81ee24d860b49b67.jpg)

[Figure](http://linoxide.com/wp-content/uploads/2016/07/CAINE.jpg)

**Network evidence collection and Analysis **

An evidence is the information to be investigated. Digital forensics analysts are dealing with different categories of evidence including  **network-based evidence**  and  **host-based evidence**. Let&#39;s start exploring how to deal with network evidence. As we cited earlier, the first step is collecting the evidence. In networking, we can perform the collection using many techniques and tools. After identifying the source of evidence using for example network diagrams, you can use packet capture tools such as:

**TCPdump **

![](RackMultipart20200926-4-4zxqee_html_c24d197499b9ae7c.png)

&quot;_Tcpdump is a powerful command-line packet analyzer; and  __libpcap__ , a portable C/C++ library for  __network traffic__  capture.&quot; (Source: tcpdump.org)_

**Wireshark **

![](RackMultipart20200926-4-4zxqee_html_6c36839be6b65087.png)

&quot;_Wireshark is the world&#39;s foremost and widely-used  __network protocol__  analyzer. It lets you see what&#39;s happening on your network at a microscopic level and is the de facto (and often de jure)  __standard__  across many commercial and non-profit  __enterprises__ ,  __government agencies__ , and educational institutions.  __Wireshark__   __development__  thrives thanks to the  __volunteer__  contributions of networking  __experts__  around the globe and is a continuation of a  __project__  started by Gerald Combs in 1998&quot;.  (Source:  __**wireshark.org**__ )_

As a demonstration let&#39;s explore how to analyse a small  **pcap**  file with Wireshark.

If you are using Kali Linux, Wireshark is already installed there.

Open Wireshark

![](RackMultipart20200926-4-4zxqee_html_b6dbf2bd8124df4f.png)

We are going to analyse this Pcap file [http\_with\_jpegs.cap.gz](https://wiki.wireshark.org/SampleCaptures?action=AttachFile&amp;do=get&amp;target=http_with_jpegs.cap.gz) from here: [https://wiki.wireshark.org/SampleCaptures](https://wiki.wireshark.org/SampleCaptures)

Open the file with Wireshark:

![](RackMultipart20200926-4-4zxqee_html_ac9803b11a2bc562.png)

To select a TCP stream go to  **Analyze**  -\&gt;  **follow TCP stream**

![](RackMultipart20200926-4-4zxqee_html_d4e9e990b92ff53f.png)

For example, we are going to extract the files from the captured packet:

Go to  **File**  -\&gt;  **Export objects**  -\&gt;  **HTTP**  -\&gt;  ** Save all**

![](RackMultipart20200926-4-4zxqee_html_cbd067afe21563a5.png)

Voila! we extracted the included files:

![](RackMultipart20200926-4-4zxqee_html_7b81776a5d623af1.png)

**Host-based evidence collection and Analysis **

As an investigator and digital forensics expert, it is essential to acquire knowledge about the different storage means and the different filesystems. By definition, a storage media is a device where we can store data and information. There are many used storage devices including:

- _Hard drive_
- _DVD-ROM_
- _USB drive_
- _Memory cards and so on _

![](RackMultipart20200926-4-4zxqee_html_89b991f2290bfff2.jpg)

[Figure](http://vskills.in/certification/blog/wp-content/uploads/2016/01/storage-devices.jpg)

The removable storage media pieces need to be formatted with a specific filesystem. Some of the most used filesystems are:

- _Ext4_
- _Ext3_
- _NTFS_
- _FAT32_

To collect host-based evidence, you need to know the difference between volatile data and non-volatile data. Volatile data is data that is lost after a shutdown or some system changes. CPU data and ARP cache are some forms of volatile data. Data stored in hard drives and Master File Table (MFT) entries are non-volatile data. The host-based evidence acquisition can be done locally or remotely. Also, it can be done online or offline. Evidence collection is performed with what we call &quot;Forensics Imaging&quot;

**Forensics Imaging **

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

![](RackMultipart20200926-4-4zxqee_html_7e91a50c4df4e13a.png)

[Figure](https://techtalk.gfi.com/wp-content/uploads/2016/02/FTK_Imager.png)

**Practical Lab 1: Autopsy Forensics Browser **

As a second demonstration, we are going to learn how to use a great forensics tool called &quot;Autopsy Forensics Browser&quot;. According to [https://www.linuxlinks.com/autopsy/](https://www.linuxlinks.com/autopsy/) :

_The Autopsy  __Forensic__   __Browser__  is a graphical  __interface__  to the  __command line__  digital  __investigation__  tools in The Sleuth Kit. The two together enable  __users__  to investigate volumes and file  __systems__  including  __NTFS__ ,  __FAT__ , UFS1/2, and Ext2/3 in a &#39;File Manager&#39; style interface and perform  __key__   __word__  searches._

If you are using Kali Linux, can found it directly there without the need to install it:

Run it from the menu:

![](RackMultipart20200926-4-4zxqee_html_aa5fa5d4170cad58.jpg)

Go to:

\&lt;a href=&quot;http://localhost:9999/autopsy&quot;\&gt;

 \&lt;a

 href=&quot;http://localhost:9999/autopsy&quot;\&gt;http://localhost:9999/autopsy

 \&lt;/a

![](RackMultipart20200926-4-4zxqee_html_f19fef6377ac0d46.png)

Create a new case:

![](RackMultipart20200926-4-4zxqee_html_89634ff226d13862.png)

Select the profile

![](RackMultipart20200926-4-4zxqee_html_5c22019c230ca11.png)

Add a host

![](RackMultipart20200926-4-4zxqee_html_cfcf024f06388f71.png)

Check the configuration and click Add Image

![](RackMultipart20200926-4-4zxqee_html_8f49e5c35446d029.png)

For the demo, we are going to use a memory dump sample (NTFS Undelete) from  [http://dftt.sourceforge.net](http://dftt.sourceforge.net/) (Digital Forensics Tool Testing Images)

![](RackMultipart20200926-4-4zxqee_html_21b5a08c6e8fdd85.png)

Add the path of the dump:

![](RackMultipart20200926-4-4zxqee_html_30b1350d06923638.png)

Click on Analyze:

![](RackMultipart20200926-4-4zxqee_html_53297c21f450e941.png)

These are some pieces of information about the dump

![](RackMultipart20200926-4-4zxqee_html_495e203d471bec32.png)

Now you can analyse the file freely:

![](RackMultipart20200926-4-4zxqee_html_8ae02b669ea19582.png)

**Practical Lab 2: Memory Analysis with Volatility **

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

\&lt;a

 class=&quot;mention&quot;

 data-id=&quot;4v8Z7sw5ifiZte6zY&quot;

 data-type=&quot;Tag&quot;

 href=&quot;/tags/wget&quot;\&gt;wget

 \&lt;a

 href=&quot;http://files.sempersecurus.org/dumps/cridex\_memdump.zip&quot;

 target=&quot;\_blank&quot;

 rel=&quot;noopener&quot;\&gt;

 \&lt;a
 href=&quot;http://files.sempersecurus.org/dumps/cridex\_memdump.zip&quot;
 target=&quot;\_blank&quot;
 rel=&quot;noopener&quot;\&gt;http://files.sempersecurus.org/dumps/cridex\_memdump.zip
 \&lt;/a

 \&lt;/a

Get info about the memory dump:

\&lt;a


 class=&quot;mention&quot;

 data-id=&quot;wAGpMrfjv7ykyEKm4&quot;

 data-type=&quot;Tag&quot;

 href=&quot;/tags/sudo&quot;\&gt;sudo

 \&lt;a
 class=&quot;mention&quot;
 data-id=&quot;bbvDjYcTgX2BDzWzp&quot;
 data-type=&quot;Tag&quot;
 href=&quot;/tags/python&quot;\&gt;python
 vol.py
 -f
 cridex.vmem
 imageinfo
 \&lt;/a

 \&lt;/a

![](RackMultipart20200926-4-4zxqee_html_782ed7e366500182.png)

Get Processes

\&lt;a class=&quot;mention&quot; href=&quot;/tags/sudo&quot; data-type=&quot;Tag&quot; data-id=&quot;wAGpMrfjv7ykyEKm4&quot; title=&quot;#sudo (search)&quot;\&gt;sudo \&lt;a class=&quot;mention&quot; href=&quot;/tags/python&quot; data-type=&quot;Tag&quot; data-id=&quot;bbvDjYcTgX2BDzWzp&quot; title=&quot;#python (search)&quot;\&gt;python vol.py -f cridex.vmem psxview\&lt;/a\&lt;/a

![](RackMultipart20200926-4-4zxqee_html_e2d844aee971e5c7.png)

Processes as Parent/Child

sudo python vol.py -f cridex.vmem pstree

![](RackMultipart20200926-4-4zxqee_html_fb365e9eb4fd8669.png)

Get hidden and terminated Processes

sudo python vol.py -f cridex.vmem psscan

![](RackMultipart20200926-4-4zxqee_html_fb365e9eb4fd8669.png)

Get DLLs

sudo python vol.py -f cridex.vmem dlllist

![](RackMultipart20200926-4-4zxqee_html_f651a381bdfb988a.png)

Get commandline args

sudo python vol.py -f cridex.vmem cmdline

![](RackMultipart20200926-4-4zxqee_html_f80667475fb2f4c4.png)

Get SIDs:

sudo python vol.py -f cridex.vmem getsids

![](RackMultipart20200926-4-4zxqee_html_a0cf712cadf6043a.png)

Networking information:

sudo python vol.py -f cridex.vmem connscan

![](RackMultipart20200926-4-4zxqee_html_ffae5424664192de.png)

Kernel modules:

sudo python vol.py -f cridex.vmem modules

![](RackMultipart20200926-4-4zxqee_html_e5ddbd3a80168e36.png)

For more information about the most used Volatility commands check these two helpful cheatsheets:

- [Volatility foundation CheatSheet\_v2.4.pdf](https://downloads.volatilityfoundation.org/releases/2.4/CheatSheet_v2.4.pdf)
- [SANS Volatility-memory-forensics-cheat-sheet.pdf](https://digital-forensics.sans.org/media/volatility-memory-forensics-cheat-sheet.pdf)

**Further Readings: **

To learn more about digital forensics I highly recommend you to explore the following posts and Wikis:

- [The cyber and digital forensics wiki](https://www.peerlyst.com/posts/the-cyber-and-digital-forensics-wiki-peerlyst?trk=search_page_search_result)
- [How to set up a secure digital forensics lab](https://www.peerlyst.com/posts/how-to-set-up-a-secure-digital-forensics-lab-sudhendu?trk=search_page_search_result)
- [So you want to be a Digital Forensics professional...](https://www.peerlyst.com/posts/so-you-want-to-be-a-digital-forensics-professional-calvin-liu?trk=search_page_search_result)
- [A definition of a digital forensics process](https://www.peerlyst.com/posts/a-definition-of-the-a-digital-forensics-process-peerlyst?trk=search_page_search_result)
- [A brief introduction to malware analysis](https://www.peerlyst.com/posts/a-brief-introduction-to-malware-analysis-kimberly-crawley?trk=search_page_search_result)

**References:**  [
](https://www.peerlyst.com/posts/how-to-perform-memory-analysis-chiheb-chebbi?trk=search_page_search_result)

- [How to Perform Memory Analysis](https://www.peerlyst.com/posts/how-to-perform-memory-analysis-chiheb-chebbi?trk=search_page_search_result)
- [https://wiki.wireshark.org/SampleCaptures](https://wiki.wireshark.org/SampleCaptures)
- [Digital Forensics and Incident Response](https://www.packtpub.com/networking-and-servers/digital-forensics-and-incident-response)
- [Digital Forensics with Kali Linux](https://www.packtpub.com/networking-and-servers/digital-forensics-kali-linux-0)

**Summary**

In this article, we discovered what digital forensics is, what are the different steps to perform it, including evidence acquisition and analysis. Later, we explored some well-known digital forensics tools by analyzing some memory dumps using Autopsy and Volatility framework.
