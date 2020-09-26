**Malware Analysis: How to use Yara rules to detect malware**

Hi Peerlysters,

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

To have a clear understanding of these techniques in detail I highly recommend that you read the first sections of my Article: &quot; **How to bypass Machine Learning Malware Detectors with Generative adversarial Networks**

Where I discussed many aspects including:

- Malware fundamentals
- Malware Distribution
- Classical AV evasion techniques
- Malware analysis techniques
- Machine learning malware detection
- Machine Learning Threat Model
- Bypassing Machine Learning malware detectors using Generative Adversarial Networks (GANs)

**Static Malware analysis**

Static malware analysis refers to the examination of the malware sample without executing it. It consists of providing all the information about the malicious binary. The first steps in static analysis are knowing the malware size and file type to have a clear vision about the targeted machines, in addition to determining the hashing values, because cryptographic hashes like MD5 or SHA1 can serve as a unique identifier for the sample file. To dive deeper, finding strings, dissecting the binary and reverse engineering the code of malware using a disassembler like IDA could be a great step to explore how the malware works by studying the program instructions. Malware authors often are trying to make the work of malware analysts harder so they are always using packers and cryptors to evade detection. That is why, during static analysis, it is necessary to detect them using tools like PEiD.

For more information, read my articles:

- [Getting started with IDA Pro](https://www.peerlyst.com/posts/getting-started-with-ida-pro-chiheb-chebbi?trk=search_page_search_result)
- [How to Perform Static Malware Analysis with Radare2](https://www.peerlyst.com/posts/how-to-perform-static-malware-analysis-with-radare2-chiheb-chebbi?trk=search_page_search_result)
- [How to build a Linux Automated Malware Analysis Lab](https://www.peerlyst.com/posts/how-to-build-a-linux-automated-malware-analysis-lab-chiheb-chebbi?trk=search_page_search_result)

In this article, we are going to explore how to use YARA Rules. When performing static malware analysis there are many techniques to classify malware and identify it such as hashes. Another technique is using YARA rules. According to Wikipedia:

&quot; **YARA**  is the name of a tool primarily used in malware research and detection. It provides a  **rule** -based approach to create descriptions of malware families based on textual or binary patterns. A description is essentially a  **Yara rule**  name, where these  **rules**

![](RackMultipart20200926-4-10yq816_html_c18cb780bb742889.jpg)

**Install Yara: **

The first step, of course, is installing YARA. If you are using Ubuntu for example, you can simply use

class=&quot;mention&quot; data-id=&quot;wAGpMrfjv7ykyEKm4&quot; data-type=&quot;Tag&quot; href=&quot;/tags/sudo&quot;\&gt;sudo apt-get class=&quot;mention&quot; data-id=&quot;yyNaYMKWDRZvHQL6q&quot; data-type=&quot;Tag&quot; href=&quot;/tags/install&quot;\&gt;install yara

It is already installed on my machine

![](RackMultipart20200926-4-10yq816_html_528576b4c6f401db.png)

Or you can download the tar file and install it from Github  [https://github.com/VirusTotal/yara/releases](https://github.com/VirusTotal/yara/releases)

tar -zxf yara-3.7.1.tar.gz

cd yara-3.7.1
 ./bootstrap.sh

./configure
 make


 \&lt;a


 class=&quot;mention&quot;

 data-id=&quot;wAGpMrfjv7ykyEKm4&quot;

 data-type=&quot;Tag&quot;

 href=&quot;/tags/sudo&quot;\&gt;sudo

 make

 install

 \&lt;/a

Yara needs the following libraries  **automake libtool make ** and  **gcc**  so ensure that you already installed them

\&lt;a class=&quot;mention&quot; href=&quot;/tags/sudo&quot; data-type=&quot;Tag&quot; data-id=&quot;wAGpMrfjv7ykyEKm4&quot; title=&quot;#sudo (search)&quot;\&gt;sudo apt-get install automake libtool make gcc\&lt;/a

![](RackMultipart20200926-4-10yq816_html_24d281af0a0ef6ab.png)

Let&#39;s check if everything went well

Create a dummy rule

class=&quot;mention&quot; data-id=&quot;ST23Jcmnioh2F7G2X&quot; data-type=&quot;Tag&quot; href=&quot;/tags/echo&quot;\&gt;echo &quot;rule dummy { condition: true }&quot; \&gt; my\_first\_rule

yara my\_first\_rule my\_first\_rule

If you get &quot; **dummy my\_first\_rule**&quot; then everything is Okay!
 ![](RackMultipart20200926-4-10yq816_html_fadbf8cf80749fe0.png)

The Official YARA documentation can be found here: [https://yara.readthedocs.io/en/stable/gettingstarted.html](https://yara.readthedocs.io/en/stable/gettingstarted.html)

**Detect Malware with Yara rules**

We already learned that we use Yara rules to detect malware. Let&#39;s discover how to do that in a real-world example. For testing purposes, I am going to use malware from a dataset called &quot;theZoo&quot;: [https://thezoo.morirt.com](https://thezoo.morirt.com/). The project owners define the repository as follows:

![](RackMultipart20200926-4-10yq816_html_41eb602bd370ab89.png)

_theZoo is a project created to make the possibility of malware analysis open and available to the public. Since we have found out that almost all versions of malware are very hard to come by in a way which will allow analysis, we have decided to gather all of them for you in an accessible and safe way. theZoo was born by Yuval tisf Nativ and is now maintained by Shahak Shalev._

_Disclaimer_

_ **Please remember that these are live and dangerous malware! They come encrypted and locked for a reason! Do NOT run them unless you are absolutely sure of what you are doing!** _

![](RackMultipart20200926-4-10yq816_html_4891cefbe46abd35.png)

Isolation is a security approach provided by many computer systems. It is based on splitting the system into smaller independent pieces to make sure that a compromised sub-system cannot affect the entire entity. Using a sandbox to analyse malware is a wise decision to run untrusted binaries. There are many sandboxes in the wild, such as Cuckoo Sandbox and LIMON, which is an open source sandbox developed by cisco systems Information Security Investigator Monnappa K A as a research project. It is a Python script that automatically collects, analyzes, and reports on Linux malware. It allows one to inspect the Linux malware before execution, during execution, and after execution (post-mortem analysis) by performing static, dynamic and memory analysis using open source tools.

To identify malware we are going to use publically available rules as a demonstration. One of the greatest resources is [https://github.com/Yara-Rules/rules](https://github.com/Yara-Rules/rules)

![](RackMultipart20200926-4-10yq816_html_6a47587c8525a972.png)

Clone them

\&lt;a class=&quot;mention&quot; href=&quot;/tags/git&quot; data-type=&quot;Tag&quot; data-id=&quot;TMLH8gEnq2rpQcJkH&quot; title=&quot;#git (search)&quot;\&gt;git clone

 \&lt;a


 href=&quot;https://github.com/Yara-Rules/rules&quot;


 target=&quot;\_blank&quot;


 rel=&quot;noopener&quot;\&gt;https://github.com/Yara-Rules/rules



 \&lt;/a\&lt;/a

![](RackMultipart20200926-4-10yq816_html_979ee212cd3ca69e.png)

_This project covers the need of a group of IT  __Security Researchers__  to have a single repository where different Yara  __signatures__  are compiled, classified and kept as up to date as possible, and began as an open source  __community__  for collecting Yara rules. Our Yara ruleset is under the GNU-GPLv2 license and open to any user or organization, as long as you use it under this license._

Yara version 3 or higher is required to run the rules.

To detect malware, generally, you need to follow this format

yara [OPTIONS] RULES\_FILE TARGET

For example to detect NJ-RAT

![](RackMultipart20200926-4-10yq816_html_83292375101124f.png)

Run the following command

yara /home/azureuser/rules/malware/RAT\_Njrat.yar /home/azureuser/malwares/theZoo/malwares/Binaries/njRAT-v0.6.4/njRAT-v0.6.4

Yara detect the malicious file

![](RackMultipart20200926-4-10yq816_html_b831fe7b93365f1d.png)

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

![](RackMultipart20200926-4-10yq816_html_9b76d31bc2e42ad8.png)

![](RackMultipart20200926-4-10yq816_html_a2af6c5c194b49cc.png)

**How to create your first YARA rule**

Let&#39;s suppose that we are going to create a rule that detects Ardamax Keylogger. First we need to extract the strings using strings command

strings ArdamaxKeylogger\_E33AF9E602CBB7AC3634C2608150DD18

![](RackMultipart20200926-4-10yq816_html_2f402826bf686e3f.png)

Select some strings for demonstration purposes. In my case I am going to select:

- _invalid bit length repeat_
- _??1type\_info@@UAE@XZ_
- _.?AVtype\_info@@_

Open a text editor and create your rule (FirstRule.yar)

rule FirstRule {

 meta:
 author = &quot;Chiheb&quot;
 last\_updated = &quot;2019&quot;
 category = &quot;Test&quot;
 confidence = &quot;medium&quot;
 description = &quot;This rule was made for a Peerlsyt Article&quot;

 strings:
 $a = &quot;invalid bit length repeat&quot; ascii wide nocase
 $b = &quot;??1type\_info@@UAE@XZ&quot; ascii wide nocase
 $c = &quot;.?AVtype\_info@@&quot; ascii wide nocase

 condition:
 ($a or $b or $c)
 }

**wide**  was added to search for strings encoded with two bytes per character

**No case**  was used to turn off the case-sensitive capability of Yara

Save the rule and run:

yara FirstRule.yar ~/malwares/theZoo/malwares/Binaries/Keylogger.Ardamax

As you can see Yara detected the malicious file based on our rules:

![](RackMultipart20200926-4-10yq816_html_a29c6cb10d4147ef.png)

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

\&lt;a

 class=&quot;mention&quot;

 data-id=&quot;TMLH8gEnq2rpQcJkH&quot;

 data-type=&quot;Tag&quot;

 href=&quot;/tags/git&quot;\&gt;git

 clone

 https://github.com/VirusTotal/yara-python


 cd

 yara-python


 python

 setup.py


 build


 sudo

 python

 setup.py

 install

 \&lt;/a

This is an example that shows how to include Yara-python in your python application:

\&gt;\&gt;\&gt; import yara
 \&gt;\&gt;\&gt; rule = yara.compile(source=&#39;rule foo: bar {strings: $a = &quot;lmn&quot; condition: $a}&#39;)
 \&gt;\&gt;\&gt; matches = rule.match(data=&#39;abcdefgjiklmnoprstuvwxyz&#39;)
 \&gt;\&gt;\&gt; print(matches)
 [foo]
 \&gt;\&gt;\&gt; print(matches[0].rule)
 foo
 \&gt;\&gt;\&gt; print(matches[0].tags)
 [&#39;bar&#39;]
 \&gt;\&gt;\&gt; print(matches[0].strings)
 [(10L, &#39;$a&#39;, &#39;lmn&#39;)]

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

I hope you will find it helpful.
