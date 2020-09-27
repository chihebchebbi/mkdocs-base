# **How to Perform Memory Analysis**

**How to Perform Memory Analysis**

![](https://lh4.googleusercontent.com/e4exMR2vLc14SOesRrLi_GMXty3_SCJjFdmwgjh4UPjbPPh_EiOOE3JtRsgS7ERSrGMROnZ_LFD9_bT3zIumLp-s3xrpLHro4jd5dyaAKYXi98lHlmhtuxX_u1QOe0kraeacwFc)

Source: [malware-analysis-virtual-box-cyber-forensicator.jpg](http://cyberforensicator.com/wp-content/uploads/2017/02/malware-analysis-virtual-box-cyber-forensicator.jpg)

**Abstract **

Hi Peerlysters! [Malware](https://www.peerlyst.com/tags/malware) [threats](https://www.peerlyst.com/tags/threats) are a very serious problem in [information security](https://www.peerlyst.com/tags/information-security) nowadays. Dangerous [hackers](https://www.peerlyst.com/tags/hackers) are inventing new [techniques](https://www.peerlyst.com/tags/techniques) on a daily basis to bypass security layers and avoid detection. Thus it is time to figure out [how to](https://www.peerlyst.com/tags/how-to) analyse [memory](https://www.peerlyst.com/tags/memory)dumps as. I already discussed briefly this technique in some of my other Peerlyst articles:

- [How to build a Linux Automated Malware Analysis Lab](https://www.peerlyst.com/posts/how-to-build-a-linux-automated-malware-analysis-lab-chiheb-chebbi?trk=search_page_search_result)
- [How To detect Advanced Volatile Threats (AVT) and Fileless Malware](https://www.peerlyst.com/posts/how-to-detect-advanced-volatile-threats-avt-and-fileless-malware-chiheb-chebbi?trk=search_page_search_result)

But this time I want to take this opportunity to elaborate more [Memory analysis](https://www.peerlyst.com/tags/memory-analysis) because it is a required skill to every [Forensics](https://www.peerlyst.com/tags/forensics) expert and malware analyst.

After reading this article you can [download](https://www.peerlyst.com/tags/download) this document that contains additional [resources](https://www.peerlyst.com/tags/resources) and tutorials: [Memory Analysis](https://static.peerlyst.com/image/upload/v1534966781/post-attachments/Memory_Analysis_bnwpk5.pdf)

In this Article we are going to learn:

- **Dissecting Memory**
- **Memory Management**
- **Computer Forensic analysis steps**
- **Digital Evidence acquisition**
- **Memory Acquisition **
- **Memory Analysis**
- **Volatility Framework **
- **Memory Analysis Best Practices**

**Memory Analysis **

[Malware analysis](https://www.peerlyst.com/tags/malware-analysis) is the art of determining the [functionality](https://www.peerlyst.com/tags/functionality), origin and potential impact of a given malware sample, such as a [virus](https://www.peerlyst.com/tags/virus), [worm](https://www.peerlyst.com/tags/worm), [trojan horse](https://www.peerlyst.com/tags/trojan-horse), [rootkit](https://www.peerlyst.com/tags/rootkit), or backdoor. As a [malware analyst](https://www.peerlyst.com/tags/malware-analyst), your main role is to collect all the information about the [malicious software](https://www.peerlyst.com/tags/malicious-software) and have a good understanding of what happened to the [infected](https://www.peerlyst.com/tags/infected) machines. Like any [process](https://www.peerlyst.com/tags/process), to perform a malware [analysis](https://www.peerlyst.com/tags/analysis) you typically need to follow a certain methodology and a number of steps.

Memory malware analysis is widely used for [digital](https://www.peerlyst.com/tags/digital) [investigation](https://www.peerlyst.com/tags/investigation) and malware analysis. It refers to the act of analysing a dumped memory image from a targeted machine after executing the malware to obtain multiple numbers of artefacts including [network](https://www.peerlyst.com/tags/network) information, running processes, [API](https://www.peerlyst.com/tags/api) hooks, [kernel](https://www.peerlyst.com/tags/kernel) loaded [modules](https://www.peerlyst.com/tags/modules), [Bash](https://www.peerlyst.com/tags/bash) history, etc. ... This phase is very important because it is always a good idea to have a clearer understanding of the malware capabilities.

- Process list and the associated threads
- [networking](https://www.peerlyst.com/tags/networking) information and interfaces (TCP/UDP) • Kernel modules including the hidden modules
- Opened files in the kernel
- Bash and commands history
- System Calls • Kernel hooks

**Dissecting Memory **

If we are going to learn how to analyse memory dumps we need first to explore what memory is? and how it works.

Memory is a vital component in the computer architecture. Computers are composed by:

- **CPU**
- **Controllers**
- **Memory**

The full architecture is described in the following graph:

![](https://lh4.googleusercontent.com/WPQnL7PehmH1VLn0uL0b6nRrxfikhloMQtWGaEFoBL1_IilQFC2UbIuNoTa-uqbtN1LOKXhuJ-xJTEebuhH5bSViHW5yfNWfSCU25FmaM0CNcOQjjnpSerGynREbEMf46dtOSlk)source [overall.gif](https://www.doc.ic.ac.uk/~eedwards/compsys/overall.gif)

In memory analysis, we are dealing with  **RAM** s.

_A  __**RAM**__  (pronounced ramm) is an acronym for random access memory, a type of computer memory that can be accessed randomly; that is, any byte of memory can be accessed without touching the preceding bytes.  __**RAM**__  is found in servers, PCs, tablets, smartphones and other _[_devices_](https://www.peerlyst.com/tags/devices)_, such as printers.  __ **RAM is volatile** _

![](https://lh4.googleusercontent.com/3K9Y2uihKcwAVuZFcrDtrhBeHey6nZeJJyDPetw_XY8X900KtlsH9IPCsMuHHn3J1K20UOhjcfx2vRomDQ16SeCQqHjovrNS7OuxdakQpqLkFyPnI0YDBJadq6DMM27CVX3WUzg)

source: [RAM061711.jpg](http://www.dfinews.com/sites/dfinews.com/files/u739/RAM061711.jpg)

The memory is divided into 4,096-byte memory chunks named pages, to facilitate internal handling. The 12 least significant bits are the offset; the rest is the page number. On the recent [x86 architecture](https://www.peerlyst.com/tags/x86-architecture), For example, the [Linux kernel](https://www.peerlyst.com/tags/linux-kernel) divides the [virtual](https://www.peerlyst.com/tags/virtual) space, usually 4 GB into 3 GB dedicated to UserLand, and 1 GB for kernel land. This operation is named segmentation. The kernel uses a page table for the correspondence between physical and virtual addresses. To manage the different regions of memory, it uses a virtual memory area (VMA)

**The stack**  is a special memory space. In [programming](https://www.peerlyst.com/tags/programming), it is an abstract data type used to collect elements using two [operations](https://www.peerlyst.com/tags/operations): [push](https://www.peerlyst.com/tags/push) and pop. This section grows automatically, but when it becomes closer to another memory section, it will cause a problem and a confusion to the system. That is why attackers are using this technique to confuse the system with other memory areas.

**The heap**  is used for dynamic memory allocation. It resides in the [RAM](https://www.peerlyst.com/tags/ram) like the stack, but it is slower. The kernel heap is using the following three types of allocators:

- **SLAB:**  This is a cache-friendly allocator.
- **A simple list of blocks (SLOB)**: This is an allocator used in small systems. It uses a first-fit algorithm.
- **SLUB** : It is the default [Linux](https://www.peerlyst.com/tags/linux) allocator.

You can explore the detailed sections of memory check this great [cheat sheet](https://www.peerlyst.com/tags/cheat-sheet):

![](https://lh4.googleusercontent.com/xndYGAhQ9AjPjqVhzFXsptsSAD0oTPc9oVSNePNF-qEu97xBVyQ1FSNaDPdmYbJ6PKM3jd3hkhBggBPtOwdo2xCTaFfFAddrCOKmd6M3zsMtB669TnLvldoYuxM6lWGCiGYdws4)

Better resolution here  [Memory Segmentation sheet ](https://www.0x0ff.info/wp-content/uploads/2014/02/cheat-sheet.png)

**Memory Management**

Memory [management](https://www.peerlyst.com/tags/management) is an important capability of every [operating](https://www.peerlyst.com/tags/operating) system. It is also integrated into Linux kernel. Linux manages memory in a virtual way. In other words, there is no correspondence between the physical memory addresses, and the addresses used and seen by the program. This technique gives the [users](https://www.peerlyst.com/tags/users) and [developers](https://www.peerlyst.com/tags/developers) flexibility. Linux is dealing with the following five types of addresses:

1. User virtual addresses
2. Physical addresses
3. Bus addresses
4. Kernel logical addresses
5. Kernel virtual addresses

**Computer Forensic analysis steps**

[NIST](https://www.peerlyst.com/tags/nist) is describing Forensics as the following:

_The most common goal of performing forensics is to gain a better understanding of an event of interest by finding and analyzing the facts related to that event... Forensics may be needed in many different situations, such as evidence collection for _[_legal_](https://www.peerlyst.com/tags/legal)_ proceedings and internal disciplinary actions, and handling of malware incidents and unusual operational problems. _

Like any methodological operation, Computer [forensic analysis](https://www.peerlyst.com/tags/forensic-analysis) goes through well-defined steps: Collection; Examination, Analysis and reporting. let&#39;s explore these steps one by one:

1. **Collection: ** identifying data ** ** sources and verify the [integrity](https://www.peerlyst.com/tags/integrity) of it
2. **Examination: ** assessing and extracting the relevant pieces of information from the collected data
3. **Analysis**
4. **Reporting**

The steps are based on the [**NIST Guide to Integrating Forensic Techniques into Incident Response**](https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-86.pdf). I highly recommend exploring the Process in details (Performing the [Forensic](https://www.peerlyst.com/tags/forensic) Process)

![](https://lh3.googleusercontent.com/Yh5H6Itbvx8GmzbYI6tfkh5IshUkXcVpeva6d6ChMX4S5188Xeg62Qkm3BLgUvOrkejbX6FpoHu1MS6NZ7W3WRthEKj1heSvEAqUpV3WBqp4HOMcdTiklpqPfNaM7Eybcz-4X20)

source: [nist+process.jpg](http://4.bp.blogspot.com/_Jgk3LbZWY8I/TL4_gGa186I/AAAAAAAAAIU/P4V8Y9lbZFo/s1600/nist+process.jpg)

**Digital Evidence acquisition **

Digital evidence needs to be treated carefully because we are going to analyse them. Also, we need to use them later within the legal process. [Eliézer Pereira](https://www.cybrary.it/members/elytech/) prioritized them in his Article [RAM Memory Forensic Analysis](https://www.cybrary.it/0p3n/ram-memory-forensic-analysis/) as the following from the most volatile to the least volatile:

- Caches
- [Routing](https://www.peerlyst.com/tags/routing) tables, process tables, memory
- Temporary system files
- Hard drive
- Remote [logs](https://www.peerlyst.com/tags/logs), [monitoring](https://www.peerlyst.com/tags/monitoring) data
- Physical network configuration, [network topology](https://www.peerlyst.com/tags/network-topology)
- Media files (CDs, DVDs)

**Memory Acquisition **

The first step of memory analysis is memory acquisition by dumping the memory of a machine using a number of utilities. One of these [tools](https://www.peerlyst.com/tags/tools) is fmem, which is a kernel module to create a new device called /dev/fmem to allow direct access to the whole memory. After downloading it from their official repository and compiling it you can acquire the machine memory using this command:

# dd if=/dev/fmem of=... bs=1MB count=...

Another [tool](https://www.peerlyst.com/tags/tool) is The Linux Memory Extractor. LIME is a Loadable Kernel Module (LKM) to allow volatile memory acquisition from Linux and Linux- based devices, such as Android. To explore LIME check this small overview: [LiME: Loadable Kernel Module Overview](https://www.peerlyst.com/posts/lime-loadable-kernel-module-overview-chiheb-chebbi?trk=search_page_search_result)

These are some [free](https://www.peerlyst.com/tags/free) Memory Acquisition tools:

- [WindowsSCOPE](http://www.windowsscope.com/)
- [https://belkasoft.com/ram-capture](https://belkasoft.com/ram-capturer)
- [**winen**](http://forensiczone.blogspot.com/2008/06/winenexe-ram-imaging-tool-included-in.html)
- [**Mdd**](https://www.forensicswiki.org/wiki/Mdd)** (Memory DD)  **(is no longer under active development.)
- [HBGary](https://www.forensicswiki.org/wiki/HBGary)


A full list of useful tools can be found here: **Tools: Memory Imaging (https://www.forensicswiki.org/wiki/Tools:Memory\_Imaging )**

After having a memory dump, it is time to analyze the memory image.

**Memory Analysis with Volatility Framework**

![](https://lh6.googleusercontent.com/Sw7Zt2Z61JUpRo56UBAYpz13Yiad_Ekkugdaen1vMICmvX0g943nJt5wqG-waTX1alVl2XSvuEpOE-VJ_PpM8Ad8NzOGhabgd7mbpPl2oYUluNmXDb5yauuJrpYaQL4nuH_goHc)

To analyse memory You can simply use volatility [framework](https://www.peerlyst.com/tags/framework), which is an [open source](https://www.peerlyst.com/tags/open-source) [memory forensics](https://www.peerlyst.com/tags/memory-forensics) tool written in Python. It is available under GPL. Volatility comes with various plugins and a number of profiles to ease obtaining basic forensic information about memory image files. To download it you can visit this website: [The Volatility Foundation - Open Source Memory Forensics](https://www.volatilityfoundation.org/) or [GitHub - volatilityfoundation/volatility](https://github.com/volatilityfoundation/volatility)

![](https://lh4.googleusercontent.com/fvGkLQLQ6PS7FkPb_el-HWvCXCbvmphmoWhWheqWryxpKAaM5cWbx-wKNDxx3oVlMONlJnnnRpCVMO6sr3mk7osnyDX-Qg3d2-vgdrFSmbEsoJolZnWqi9z7o6MiLoUFYgFv9T4)

source: [volatility-sockets.gif](https://xerocrypt.files.wordpress.com/2014/06/volatility-sockets.gif)

To identify [malicious](https://www.peerlyst.com/tags/malicious) network activities many experts recommend following these steps. First, you can identify Process IDs of network connections.

![](https://lh6.googleusercontent.com/4RBMs4CbDRoyfVc5TXg-g6sYJmoPZVvVLSrkv6B4KYXT-x2AJBFvNk2bXUj6MFvMeISyaTs92mR2fUvRRRnh_fiRuAx5V7aKVyL1mLxFQXhi_BvYHd13QXxZBDeI9dPLE1PL53A)

source: [pslist.png](https://linoxide.com/wp-content/uploads/2016/07/pslist.png)

Later you need to map that IDs to Process Names and later terminate every step and process by collecting the artefacts by taking notes, screenshots and of [course](https://www.peerlyst.com/tags/course) time-stamps.

![](https://lh5.googleusercontent.com/V9xhfPWZOAERwFE0fziWTxzIiPT5vG25ob_Ce5SdEZEcvVAPm-6brmif0riGPJdfaieUVTdKz-b7JolDFoW1d3La9LILmTIqfrvVDK-TwgfuS7wpeEdU4eLgKuN2YhHK5Jwt58k)

source: [Fig2lg061711.jpg](http://www.dfinews.com/sites/dfinews.com/files/u739/Fig2lg061711.jpg)

**Note: ** this section is not completed yet. The processes will be described in a detailed way. Stay tuned.

**Peerlyst Articles about Memory Analysis you need to explore**

- [Useful PhD thesis: Advances in Modern Malware and Memory Analysis - contains 4 new proposals](https://www.peerlyst.com/posts/useful-phd-thesis-advances-in-modern-malware-and-memory-analysis-contains-4-new-proposals-karl-m-1?trk=search_page_search_result)
- [Some useful forensics tools for your forensics investigation](https://www.peerlyst.com/posts/some-useful-forensics-tools-for-your-forensics-investigation-adminadmin?trk=search_page_search_result)
- [How to build a Linux Automated Malware Analysis Lab](https://www.peerlyst.com/posts/how-to-build-a-linux-automated-malware-analysis-lab-chiheb-chebbi?trk=search_page_search_result)
- [LiME: Loadable Kernel Module Overview](https://www.peerlyst.com/posts/lime-loadable-kernel-module-overview-chiheb-chebbi?trk=search_page_search_result)
- [Malware analysis Frameworks](https://www.peerlyst.com/posts/malware-analysis-frameworks-prasanna-b-mundas?trk=search_page_search_result)
- [Memory Forensics : Tracking Process Injection](https://www.peerlyst.com/posts/memory-forensics-tracking-process-injection-saurabh-sharma?trk=search_page_search_result)

**Volatility Peerlyst Articles:**

- [How to Perform Forensic Analysis with Volatility – Part 1](https://www.peerlyst.com/posts/forensic-analysis-with-volatility-part-1-abhinav-singh?trk=search_page_search_result)
- [How to Perform Forensic Analysis with Volatility – Part 2](https://www.peerlyst.com/posts/how-to-perform-forensic-analysis-with-volatility-part-2-abhinav-singh?trk=search_page_search_result)
- [The Volatility wiki](https://www.peerlyst.com/posts/the-volatility-wiki-peerlyst?trk=search_page_search_result)

**Summary **

In this article, we explored how to perform Malware memory analysis.

**Post Updates**

Checked the availability of tools (Thanks to  **Ken Pryor** )

**References**

1. [https://technical.nttsecurity.com/post/102egyy/hunting-malware-with-memory-analysis](https://technical.nttsecurity.com/post/102egyy/hunting-malware-with-memory-analysis)
2. Advanced Infrastructure [Penetration Testing](https://www.peerlyst.com/tags/penetration-testing) Chiheb Chebbi
3. [https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-86.pdf](https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-86.pdf)
4. [https://www.cybrary.it/0p3n/ram-memory-forensic-analysis/](https://www.cybrary.it/0p3n/ram-memory-forensic-analysis/)
5. [https://resources.infosecinstitute.com/memory-forensics/#gref](https://resources.infosecinstitute.com/memory-forensics/#gref)
6. [https://technical.nttsecurity.com/post/102egyy/hunting-malware-with-memory-analysis](https://technical.nttsecurity.com/post/102egyy/hunting-malware-with-memory-analysis)
7. [What is RAM - Random Access Memory? Webopedia Definition](https://www.webopedia.com/TERM/R/RAM.html)
