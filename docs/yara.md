# Malware Analysis: How to use Yara rules to detect malware


When performing malware analysis, the analyst needs to collect every piece of information that can be used to identify malicious software. One of the techniques is Yara rules. In this article, we are going to explore Yara rules and how to use them in order to detect malware.

The article outline is the following:

- What is malware analysis
- Static malware analysis techniques
- What is Yara and how to install it
- Detect malware with Yara
- Yara rule structure
- How to write your first Yara rule
- Yara-python

After reading this article you can download this small document that includes other helpful resources: [Yara Rules Resources](https://static.peerlyst.com/image/upload/v1571381124/post-attachments/Yara_Rules_Resources_unj0lm)

**Malware Analysis**

Malware is a complex and malicious piece of software.Its behavior range from basic actions like simple modifications of computer systems to advanced behaviors patterns.

By definition, a malware is a malicious piece of software with the aim of damaging computer systems like data andidentity stealing ,espionage,legitimate users infection and gaining full or limited control to its developer.To have a clear understanding of malware analysis, a malware categorization based on its behavior is a must. Even sometimes we cannot classify a malware because it uses many different functionalities but in general, malware can be divided into many categories some of them are described below:

- **Trojan:**  is a malware that appears as a legitimate application
- **Virus:**  this type of malware copy itself and infect computer machines
- **Botnets ** are networks of compromised machines which are generally controlled by a command and control (C2C) channel
- **Ransomware**  this malware encrypts all the data on a computer and ask the victim usually using the cryptocurrency Bitcoin to get the decryption key
- **Spyware**  as it is obvious from the name it is a malware that tracks all the user activities including Search history,installed applications
- **Rootkit**  enables the attacker to gain an unauthorized access generally administrative to a system.Basically, it is unnoticeable and makes its removal as hard as possible

Malware analysis is the art of determining the functionality, origin and potential impact of a given malware sample, such as a virus, worm, trojan horse, rootkit, or backdoor. As a malware analyst, our main role is to collect all the information about malicious software and have a good understanding of what happened to the infected machines. Like any process, to perform a malware analysis we typically need to follow a certain methodology and a number of steps. To perform Malware Analysis we can go thru three phases:

- Static Malware Analysis
- Dynamic Malware Analysis
- Memory Malware Analysis


**Static Malware analysis**

Static malware analysis refers to the examination of the malware sample without executing it. It consists of providing all the information about the malicious binary. The first steps in static analysis are knowing the malware size and file type to have a clear vision about the targeted machines, in addition to determining the hashing values, because cryptographic hashes like MD5 or SHA1 can serve as a unique identifier for the sample file. To dive deeper, finding strings, dissecting the binary and reverse engineering the code of malware using a disassembler like IDA could be a great step to explore how the malware works by studying the program instructions. Malware authors often are trying to make the work of malware analysts harder so they are always using packers and cryptors to evade detection. That is why, during static analysis, it is necessary to detect them using tools like PEiD.


In this article, we are going to explore how to use YARA Rules. When performing static malware analysis there are many techniques to classify malware and identify it such as hashes. Another technique is using YARA rules. According to Wikipedia:

&quot; **YARA**  is the name of a tool primarily used in malware research and detection. It provides a  **rule** -based approach to create descriptions of malware families based on textual or binary patterns. A description is essentially a  **Yara rule**  name, where these  **rules**

![](https://lh3.googleusercontent.com/9vjOkN0oLeIrqDd-lsLffyuUJO5P---Hnpx5UdWyXRP-asHzm0Cs_cE_Iey31HlNF4NdHO6o0bxED_n1LJRlVSaSd3AjxFOrnXJ8zu1lK_ANrbP_qEJ67Dlldko8qB-x2gXVzGs)

**Install Yara: **

The first step, of course, is installing YARA. If you are using Ubuntu for example, you can simply use

`sudo apt-get install yara`

It is already installed on my machine

![](https://lh4.googleusercontent.com/FhM76efi8q23Vh_JPIeWoHQcInQkQWMWnhXwlZ377fVwTpNfS8sHTVuKqv8L8xjB6G47mXvy2wglk-A4EZQkUv5vUPY4COL45G-eLaPEVs3c1eyk_arK8-x2R84H-3MdREXdg2w)

Or you can download the tar file and install it from Github  [https://github.com/VirusTotal/yara/releases](https://github.com/VirusTotal/yara/releases)

`tar -zxf yara-3.7.1.tar.gz`

`cd yara-3.7.1`

`./bootstrap.sh`
`./configure`
` make`
`make install`

Yara needs the following libraries  **automake libtool make ** and  **gcc**  so ensure that you already installed them

`sudo apt-get install automake libtool make gcc`

![](https://lh5.googleusercontent.com/97yuOIin2zhOWE4hbyjUTc9HuWmeX7jcbDWB2S8qhn1M1IHIF2SMzcLL-KLY_Pch-UuWxk35nfpzXXM4pExJXY01mhxXUagL71N_POYatIkilqYWEnZKt0Qdh_nd7IXWhCrlDGM)

Let&#39;s check if everything went well

Create a dummy rule

`echo "rule dummy { condition: true }" > my_first_rule`

`yara my_first_rule my_first_rule`

If you get &quot; **dummy my\_first\_rule**&quot; then everything is Okay!
 ![](https://lh5.googleusercontent.com/sPlFO0N1mGsp6XTjitOLCqzFja5eQMTzg7xg6saP1YsnxRxINdxqJB04_hFXbeLaPZXGAYHai-JJeZjLwUb9ry0T_pjLPbq6jIHLpu7ljwIAUalW_n_Gdt-vhbja5pP8uKvIa_Y)

The Official YARA documentation can be found here: [https://yara.readthedocs.io/en/stable/gettingstarted.html](https://yara.readthedocs.io/en/stable/gettingstarted.html)

**Detect Malware with Yara rules**

We already learned that we use Yara rules to detect malware. Let&#39;s discover how to do that in a real-world example. For testing purposes, I am going to use malware from a dataset called &quot;theZoo&quot;: [https://thezoo.morirt.com](https://thezoo.morirt.com/). The project owners define the repository as follows:

![](https://lh3.googleusercontent.com/D2zmI8sO6J2NLxxvsuKa5ZNeaHGC1VB_r4Y1q5xrv6Kjr_0dze156i6UrYLUk8eyVDC1SGhK_p79T3kdP7I5Ztr61-kxb3TGtqwg8Wh2ENPhIPyKAiBShy6-NKiGlxEXEBXBVug)

_theZoo is a project created to make the possibility of malware analysis open and available to the public. Since we have found out that almost all versions of malware are very hard to come by in a way which will allow analysis, we have decided to gather all of them for you in an accessible and safe way. theZoo was born by Yuval tisf Nativ and is now maintained by Shahak Shalev._

_Disclaimer_

_ **Please remember that these are live and dangerous malware! They come encrypted and locked for a reason! Do NOT run them unless you are absolutely sure of what you are doing!** _

![](https://lh4.googleusercontent.com/FilhWX4M06-sE7UlCrBP82MvVefUCT0UQQhjzHi4F46lvKUqUs1BNorxcpUB1enkdHMUXbqCV1HCygjGe4y4Vv_SK_GlbOnlxNiEg4-My2SHJyfO6S4kNpxKl-HSo_1HBrhoa0I)

Isolation is a security approach provided by many computer systems. It is based on splitting the system into smaller independent pieces to make sure that a compromised sub-system cannot affect the entire entity. Using a sandbox to analyse malware is a wise decision to run untrusted binaries. There are many sandboxes in the wild, such as Cuckoo Sandbox and LIMON, which is an open source sandbox developed by cisco systems Information Security Investigator Monnappa K A as a research project. It is a Python script that automatically collects, analyzes, and reports on Linux malware. It allows one to inspect the Linux malware before execution, during execution, and after execution (post-mortem analysis) by performing static, dynamic and memory analysis using open source tools.

To identify malware we are going to use publically available rules as a demonstration. One of the greatest resources is [https://github.com/Yara-Rules/rules](https://github.com/Yara-Rules/rules)

![](https://lh3.googleusercontent.com/i6UZdcQJF-Ezk01w5j-x2IQBdbFCz6J9iBCBrXx8l3ANQDv0cQtceOCZncBZHfAC8BQ10G1y3CGuZBksjH0AfmKzscl3YrcEzqJLtT2yP_TnTK06UfjnSRe7waJNMkyG6nCgRZw)

Clone them

`git clone https://github.com/Yara-Rules/rules`

![](https://lh4.googleusercontent.com/fVpeCDF9nTax0lkufte1DWj2_U31Ca24pK5_eumqmLIGqJMEdEg4CWhEcRYOXUzzxW5K8r3AKQf2EWuScaVlcVMwhfTuFFXh8iAGrOjWqkKarHEgyyAwpc-vhfmyyR5KgDkle2U)

_This project covers the need of a group of IT  __Security Researchers__  to have a single repository where different Yara  __signatures__  are compiled, classified and kept as up to date as possible, and began as an open source  __community__  for collecting Yara rules. Our Yara ruleset is under the GNU-GPLv2 license and open to any user or organization, as long as you use it under this license._

Yara version 3 or higher is required to run the rules.

To detect malware, generally, you need to follow this format

`yara [OPTIONS] RULES_FILE TARGET`

For example to detect NJ-RAT

![](https://lh3.googleusercontent.com/ZxM_Abol2c3x_n2ydrC_VRALZ2c5OjCAvmA3fz4qNozWXv4psWBa81BFd0759aagDCwx7GoFfIQ8y_lHhRPHqcqOzmXEc_ol4u1fX6SnjolXB04hYqigmnds4dpHs7cLdmEQGoI)

Run the following command

`yara /home/azureuser/rules/malware/RAT\_Njrat.yar /home/azureuser/malwares/theZoo/malwares/Binaries/njRAT-v0.6.4/njRAT-v0.6.4`

Yara detect the malicious file

![](https://lh6.googleusercontent.com/zQorO0zrUjcogLz7o3adoPJIB1SG18AiNGCGQJIjWqll0crUMTy-D5-GObdAIx7tGA9s2pbYyGIjkmaQCRrm_BqvBFgC8o5nwZ9yT4HX66ElH1ERGiyv2eiognjvPDb4Iq07wbw)

**Yara Rules structure**

Now let&#39;s explore the structure of a Yara rule. Yara rules usually contain:

- Metadata: Information about the rule (Author, development date and so on)
- **Identifiers **
- **Strings identification: ** You need to add the strings that YARA needs to look for in order to detect malware.
- **Condition: ** this is a logical rule to detect the identified strings and indicators.

For example, this is a skeleton of a simple Yara rule:

    rule Malware\_Detection
     {
     strings:
     $a = &quot;Sring1&quot;
     $b = &quot;String2&quot;
    
     condition:
     ($a or $b)
     }

You can&#39;t use these terms as identifiers:

_all, and, any, ascii, at, condition, contains,entrypoint, false, filesize, fullword, for, global, in ,import, include, int8, int16, int32, int8be, int16be,int32be, matches, meta, nocase, not, or, of,private, rule, strings, them, true, uint8, uint16,uint32, uint8be, uint16be, uint32be, wide_

This is the Yara rule for the njRAT detection

![](https://lh6.googleusercontent.com/re74iFErB_sdTpmREiEKiZ689AqI8MGTtyVfD4jFWkVUtqetUnwyYRyhyhksn_bdfRXR8ZFNz04eriqqj1dOnZd2UtjfePSZp5f8jQ-wjykHWqihKb5tdPQbKX1uFTdSnoXYpL8)

![](https://lh3.googleusercontent.com/AgRpHGoSBWlQi5l4t89xOweO13iePdy_aI_h-9tmeGwjb2M-HneuTyLDU5trO9IpVULHblvnjZaBevtTx8i5JCCuTskbC_pM-MQjRDoU_FRUAKAVfeGSnLvFnF_MUTRXIl-rGig)

**How to create your first YARA rule**

Let&#39;s suppose that we are going to create a rule that detects Ardamax Keylogger. First we need to extract the strings using strings command

`strings ArdamaxKeylogger_E33AF9E602CBB7AC3634C2608150DD18`

![](https://lh3.googleusercontent.com/jvRQj3QJvsi0w-K7Y5yUKV3OjNQKxHlViASGNHdvyL4La9JKAGJFwDRh4VUzjoauMpJHqXK4ujnpO0gI2sxIVE3D-d7215_OcCAktsABkUwdQHYGC6tZqQ_1RnlYMw84G_IOvtM)

Select some strings for demonstration purposes. In my case I am going to select:

- _invalid bit length repeat_
- _??1type\_info@@UAE@XZ_
- _.?AVtype\_info@@_

Open a text editor and create your rule (FirstRule.yar)

    rule FirstRule {
    
    meta:
      author = "Chiheb"
      last_updated = "2019"
      category = "Test"
      confidence = "medium"
      description = "This rule was made for a Peerlsyt Article"
    
    strings:
      $a = "invalid bit length repeat" ascii wide nocase
      $b = "??1type_info@@UAE@XZ" ascii wide nocase
      $c = ".?AVtype_info@@" ascii wide nocase
    
    condition:
     ($a or $b or $c)
    }

**wide**  was added to search for strings encoded with two bytes per character

**No case**  was used to turn off the case-sensitive capability of Yara

Save the rule and run:

`yara FirstRule.yar ~/malwares/theZoo/malwares/Binaries/Keylogger.Ardamax`

As you can see Yara detected the malicious file based on our rules:

![](https://lh4.googleusercontent.com/Pqvj7lQxYmBMhk2Dzy4oPVlOblpUtLZM_LE6F4OqUT0TYW_2fSN7VBr2VXoL_7w4cHCZUNBkLqAWNFfFnbRHAKdJQ7AfAqrv_vVqkRk4hygz1QrO30vmVr8o-OwZxeFfXg7Z3NQ)

Yara supports regular expressions thus you can use one of the following expressions

| \* | Match 0 or more times |
| --- | --- |
| + | Match 1 or more times |
| ? | Match 0 or 1 time  |
| {n} | Match exactly n times |
| {n,} | Match at least n times |
| {,m} | Match 0 to m times |
| {n,m} | Match n to m times |

**Yara Python**

It is possible to add Yara capabilities to your python API thanks to a library called &quot;Yara-Python&quot;.

_With this library you can use _[_YARA_](https://github.com/VirusTotal/yara)_ from your Python programs. It covers all YARA&#39;s features, from compiling, saving and loading rules to  __scanning__  files, strings and processes._

To install it:

` clone https://github.com/VirusTotal/yara-python`

` cd yara-python`

` python setup.py build`

` sudo python  setup.py install`

This is an example that shows how to include Yara-python in your python application:

    >>> import yara
    >>> rule = yara.compile(source='rule foo: bar {strings: $a = "lmn" condition: $a}')
    >>> matches = rule.match(data='abcdefgjiklmnoprstuvwxyz')
    >>> print(matches)
    [foo]
    >>> print(matches[0].rule)
    foo
    >>> print(matches[0].tags)
    ['bar']
    >>> print(matches[0].strings)
    [(10L, '$a', 'lmn')]

**Evasion techniques**

Black hat Hackers are highly intelligent people. That is why they are looking every day for methods to escape antiviruses and avoid detection.Antiviruses are not  totally protection solutions. All the AV vendors are failing to detect advanced persistent attacks no matter how sophisticated their solutions are. Attackers are using many means and tactics to bypass Antivirus protection. Below are some methods used to fool the antiviruses:

- **Obfuscation**  is a technique used to make the textual structure of a malware binary hard to read as much as possible. In malware development world is vital to hide what we call the strings. Strings are significant words usually are URLs, registry keys etc.. To do this, cryptographic standards are used in many cases to achieve this task
- **Binding**  is the operation of binding the malware into another legitimate application
- **Crypters and packers**  are tools and techniques used to encrypt a malware and keep the antivirus away from peeking inside. Packers some time called executable compression methods are used to make reverse engineering more difficult.

**Summary**

By now, we explored what is the different malware analysis approaches after a small overview of some types of malicious pieces of software. Later we start exploring Yara rules, their structures, how to detect malware with them and how to create your own first Yara rule. Then we discovered the python interface of Yara. Finally, we learned some AV evasion techniques.

**References and further reading: **

1. [https://www.real0day.com/hacking-tutorials/yara](https://www.real0day.com/hacking-tutorials/yara)
2. [https://0x00sec.org/t/tutorial-creating-yara-signatures-for-malware-detection/5453](https://0x00sec.org/t/tutorial-creating-yara-signatures-for-malware-detection/5453)
3. [https://github.com/VirusTotal/yara-python](https://github.com/VirusTotal/yara-python)
4. [https://seanthegeek.net/257/install-yara-write-yara-rules/](https://seanthegeek.net/257/install-yara-write-yara-rules/)
5. [https://yara.readthedocs.io/en/v3.4.0/writingrules.html](https://yara.readthedocs.io/en/v3.4.0/writingrules.html)



