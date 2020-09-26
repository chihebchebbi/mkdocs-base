Hi Peerlysters,

 In this article, we are going to explore how to perform static malware analysis with Radare2.

![](RackMultipart20200926-4-1w5ysxb_html_7feb5e9362c92fc0.jpg)

[source](https://pbs.twimg.com/media/Ddzn6oSVwAAXZOq.jpg)

Before diving into technical details let&#39;s explore first what is malware analysis and what are the different approaches to perform it.

 Malware analysis is the art of determining the functionality, origin and potential impact of a given malware sample, such as a virus, worm, trojan horse, rootkit, or backdoor. As a malware analyst, our main role is to collect all the information about malicious software and have a good understanding of what happened to the infected machines. Like any process, to perform a malware analysis we typically need to follow a certain methodology and a number of steps. To perform Malware Analysis we can go through three phases:

- Static Malware Analysis
- Dynamic Malware Analysis
- Memory Malware Analysis

**Static Malware analysis **

Static malware analysis refers to the examination of the malware sample without executing it. It consists of providing all the information about the malicious binary. The first steps in the static analysis are knowing the malware size and file type to have a clear vision about the targeted machines, in addition to determining the hashing values, because cryptographic hashes like MD5 or SHA1 can serve as a unique identifier for the sample file. To dive deeper, finding strings, dissecting the binary and reverse-engineering the code of malware using a disassembler like IDA could be a great step to explore how the malware works by studying the program instructions. Malware authors often are trying to make

the work of malware analysts harder so they are always using packers and cryptors to evade detection. That is why, during static analysis, it is necessary to detect them using tools like PEiD.

**Dynamic Malware analysis **

Performing static analysis is not enough to fully understand malware&#39;s true functionality. That is why running the malware in an isolated environment is the next step for the malware analysis process. During this phase, the analyst observes all the behaviours of the malicious binary. Dynamic analysis techniques track all the malware activities, including DNS summary, TCP connections, network activities, syscalls and much more.

**Memory Malware analysis **

Memory malware analysis is widely used for digital investigation and malware analysis. It refers to the act of analysing a dumped memory image from a targeted machine after executing the malware to obtain multiple numbers of artefacts including network information, running processes, API hooks, kernel loaded modules, Bash history, etc. ... This phase is very important because it is always a good idea to have a clearer understanding of malware capabilities. The first step of memory analysis is memory acquisition by dumping the memory of a machine using a various number of utilities. One of these tools is fmem, which is a kernel module to create a new device called /dev/fmem to allow direct access to the whole memory

To perform malware analysis you need to build a malware lab. To learn how to do it, I highly recommend you to read my article:

**How to perform static malware analysis with Radare2**

According to its official

[Github](https://github.com/radare/radare2) account:

_Radare2 __ is unix-like __ reverse engineering __ __ framework __ and __ command line__ tools_

![](RackMultipart20200926-4-1w5ysxb_html_c64ab1af6bc0dfcb.png)

Source:  [https://rada.re/r/img/webui.png](https://rada.re/r/img/webui.png)

It is more than a reverse engineering tool. R2 is able to perform many other tasks. Usually, you will find it hard to learn Radare2 but after a while, you will acquire a good understanding of most of its features.

![](RackMultipart20200926-4-1w5ysxb_html_fd0cb3488f8d5f81.png)

[Source](https://radare.gitbooks.io/radare2book/content/first_steps/learning_curve.png)

Let&#39;s get started by exploring this great tool. As a demonstration, we are going to learn how to perform some static malware analysis with it. Usually, in the static analysis, we need to perform these tasks and to collect many pieces of  information including:

- File type and architecture
- File fingerprinting and hashes
- Strings
- Decoding obfuscation
- Determining Packers and Cryptors
- Header information
- Classification and Yara Rules
- Online AV Scanning (Check the embedded article for more information)

**Radare2 installation:**

Before using R2 we need to install it first.

$ \&lt;a class=&quot;mention&quot; data-id=&quot;TMLH8gEnq2rpQcJkH&quot; data-type=&quot;Tag&quot; href=&quot;/tags/git&quot;\&gt;git clone \&lt;a href=&quot;https://github.com/radare/radare2.git&quot; target=&quot;\_blank&quot; rel=&quot;noopener&quot;\&gt;https://github.com/radare/radare2.git\&lt;/a\&lt;/a

cd radare2

and install it:

$ sys/install.sh

Radare2 contains many tools such as  **rabin2** ,  **radiff2** , **rax2** ,  **rasm2**  etc...

If you are using Kali Linux you can use it directly by typing:

r2

![](RackMultipart20200926-4-1w5ysxb_html_dcc5022d3b1f5179.png)

For the demonstration, I downloaded &quot;[Multi-Platform Linux Router DDoS ELF](http://blog.malwaremustdie.org/2014/05/threat-analysis-zendran-elf-ddos-scheme.html)&quot;.

 As discussed previously first we need to obtain information about the binary:

rabin2 -I halfnint

![](RackMultipart20200926-4-1w5ysxb_html_5f58ba1e409305ce.png)

To extract the string from the data section type:

rabin2 -z halfnint

![](RackMultipart20200926-4-1w5ysxb_html_c15a56f6f0dbd78c.png)

Load the binary

radare2 halfnint

To get information use the &quot; ** i **&quot; option. Check all the available gathered information by typing:

i?

![](RackMultipart20200926-4-1w5ysxb_html_c00d5a1fd54de76e.png)

For example to collect information about Exports type:

iE

![](RackMultipart20200926-4-1w5ysxb_html_6795461d9f5c9234.png)

Imports:

ii

![](RackMultipart20200926-4-1w5ysxb_html_7ba0335ac811987c.png)

Headers:

ih

![](RackMultipart20200926-4-1w5ysxb_html_568b05c223a0e3ff.png)

To calculate the hashes type:

rahash2 -a all halfnint

![](RackMultipart20200926-4-1w5ysxb_html_72023ccbaaf53163.png)

To determine the packers usually, we use [PEiD](https://www.aldeid.com/wiki/PEiD)

![](RackMultipart20200926-4-1w5ysxb_html_693853757d583d70.png)

[source](https://www.aldeid.com/w/images/c/c6/Peid.png)

But it is a bit outdated, thus, There is Yara [support](https://github.com/radare/radare2/issues/8241) in r2 and PEiD signatures are available in Yara format.

install  **libyara**

r2pm init

r2pm -i yara3-lib

Some other useful resources:

- [Resource: Malware analysis - learning How To Reverse Malware: A collection of guides and tools](https://www.peerlyst.com/posts/resource-learning-how-to-reverse-malware-a-guide?trk=search_page_search_result)
- [A Malware Analysis wiki](https://www.peerlyst.com/posts/a-malware-analysis-wiki-peerlyst?trk=search_page_search_result)[
](https://github.com/dukebarman/awesome-radare2)
- [Malware Analysis](https://www.peerlyst.com/posts/malware-analysis?trk=search_page_search_result)
- [My new course: Reverse Engineering with Radare2](https://www.peerlyst.com/posts/my-new-course-reverse-engineering-with-radare2-gergely-rvay?trk=search_page_search_result) by  Gergely Révay‍
- [https://github.com/dukebarman/awesome-radare2](https://github.com/dukebarman/awesome-radare2)

**Summary**

In this article, we explored the different techniques to perform malware analysis. Later we learned how to install an amazing tool called &quot;Radare2&quot; and how to use to perform some static malware analysis tasks.

**References:**

[1] Chiheb Chebbi &quot;Malware Analysis a Machine Learning Approach&quot; eForensics Magazine Issue 07/2017

[2] Chiheb Chebbi: How to bypass Machine Learning Malware Detectors with Generative adversarial Networks -Peerlyst

[3] [https://github.com/radare/radare2/blob/master/doc/yara.md](https://github.com/radare/radare2/blob/master/doc/yara.md)
