# **Vulnerability Scanning**

In this chapter, we are going to deal with an important step and [operation](https://www.peerlyst.com/tags/operation) in information security which is [vulnerability](https://www.peerlyst.com/tags/vulnerability) scanning. Thus, we will explore [how to](https://www.peerlyst.com/tags/how-to) [scan](https://www.peerlyst.com/tags/scan) [Linux systems](https://www.peerlyst.com/tags/linux-systems) in order to find hidden vulnerabilities. Also we will discuss vulnerability assessment, [vulnerability management program](https://www.peerlyst.com/tags/vulnerability-management-program) and policies.

 First let&#39;s define the most important [terminology](https://www.peerlyst.com/tags/terminology) here, vulnerability. Vulnerability is a known [weakness](https://www.peerlyst.com/tags/weakness) or a [gap](https://www.peerlyst.com/tags/gap) in an asset.

![](RackMultipart20200926-4-r9r9dm_html_cd41a4bfee9c44d9.jpg)

[security-vulnerability-Shutterstock-Andy-Dean-Photography-601x513-568x485.jpg](https://www.mobiusleadership.com/wp-content/uploads/2019/07/security-vulnerability-Shutterstock-Andy-Dean-Photography-601x513-568x485.jpg)

According to [techtarget](https://searchsecurity.techtarget.com/definition/vulnerability-scanning):

[_Vulnerability scanning_](https://www.peerlyst.com/tags/vulnerability-scanning)_  __is an inspection of the potential points of__  _[_exploit_](https://www.peerlyst.com/tags/exploit)_  __on a computer or__  _[_network_](https://www.peerlyst.com/tags/network)_  __to identify security holes. A vulnerability__  _[_scanner_](https://www.peerlyst.com/tags/scanner)_  __detects and classifies system__  _[_weaknesses_](https://www.peerlyst.com/tags/weaknesses)_  __in__  _[_computers_](https://www.peerlyst.com/tags/computers)_,__ _[_networks_](https://www.peerlyst.com/tags/networks)_ __and__ _[_communications_](https://www.peerlyst.com/tags/communications)_ __equipment and predicts the effectiveness of countermeasures._

As a hand-on demonstration, we are going to use a well-known vulnerability scanner called &quot;OpenVAS&quot;

![](RackMultipart20200926-4-r9r9dm_html_fb0fc8149da87343.png)

![](RackMultipart20200926-4-r9r9dm_html_7b6148bc7c92d6f5.png)

[29148d80eb45406d8d65fadd5208dabf9516c2e3.jpeg](https://community.greenbone.net/uploads/default/original/1X/29148d80eb45406d8d65fadd5208dabf9516c2e3.jpeg)

I am going to [install](https://www.peerlyst.com/tags/install), configure and use [OpenVAS](https://www.peerlyst.com/tags/openvas) on [Kali Linux](https://www.peerlyst.com/tags/kali-linux) machine. If you want to learn how to install [Kali](https://www.peerlyst.com/tags/kali), I highly recommend you to read my article: [[Mastering Kali Linux] Chapter 1: Introduction to Ethical Hacking and Penetration Testing](https://www.peerlyst.com/posts/mastering-kali-linux-chapter-1-introduction-to-ethical-hacking-and-penetration-testing-chiheb-chebbi?trk=search_page_search_result)

Start by:

\&lt;a class=&quot;mention&quot; href=&quot;/tags/sudo&quot; data-type=&quot;Tag&quot; data-id=&quot;wAGpMrfjv7ykyEKm4&quot; title=&quot;#sudo (search)&quot;\&gt;sudo apt \&lt;a class=&quot;mention&quot; href=&quot;/tags/update&quot; data-type=&quot;Tag&quot; data-id=&quot;Fk3AXWcx9jLz9ZNAz&quot; title=&quot;#update (search)&quot;\&gt;update\&lt;/a\&lt;/a

![](RackMultipart20200926-4-r9r9dm_html_c4a27313ecbf6650.png)

Now install the vulnerability scanner:

sudo apt-get install openvas

![](RackMultipart20200926-4-r9r9dm_html_7e90e40774d4dc31.png)

![](RackMultipart20200926-4-r9r9dm_html_90b39b88c55bf0d2.png)

![](RackMultipart20200926-4-r9r9dm_html_927fdcb91799b44a.png)

After the installation, you need to configure it:

sudo openvas-setup

![](RackMultipart20200926-4-r9r9dm_html_49f13678680ca285.png)

![](RackMultipart20200926-4-r9r9dm_html_3f9b059175ee0e44.png)

To enter the scanner via the [web interface](https://www.peerlyst.com/tags/web-interface) just type:

\&lt;IP\&gt;:9392

![](RackMultipart20200926-4-r9r9dm_html_2c46cb28fbe843a7.png)

Voila! Now you just need to add the target and start the scan.

 The following is an example of a resulted [report](https://www.peerlyst.com/tags/report) by [Bujarra](http://www.bujarra.com/wp-content/uploads/2017/08/openvas-12.png):

![](RackMultipart20200926-4-r9r9dm_html_62890566caf33d3a.png)To avoid any confusion we need to know the difference between  **Vulnerability scanning**  and ** **** vulnerability assessment**:

## Vulnerability assessment

[vulnerability assessment](https://www.peerlyst.com/tags/vulnerability-assessment) is the [process](https://www.peerlyst.com/tags/process) of identifying, measuring, and classifying vulnerabilities in an information system. Vulnerability [analysis](https://www.peerlyst.com/tags/analysis) is a critical [skill](https://www.peerlyst.com/tags/skill) for every pentester.

There is a big misunderstanding when it comes to vulnerability assessment. Many [penetration](https://www.peerlyst.com/tags/penetration) testers confuse [vulnerability analysis](https://www.peerlyst.com/tags/vulnerability-analysis)with penetration testing. In fact, [penetration testing](https://www.peerlyst.com/tags/penetration-testing) is simulating an [attack](https://www.peerlyst.com/tags/attack), whereas vulnerability assessment is intended to identify vulnerabilities in a specific area. You can view it as a [scanning](https://www.peerlyst.com/tags/scanning) operation.

## Vulnerability Management program

According to [Rapid7](https://www.rapid7.com/fundamentals/vulnerability-management-and-scanning/)

&quot;_Vulnerability management __ __ is the process of identifying, evaluating, treating, and reporting on security vulnerabilities in systems and the software that runs on them. __ __ Security vulnerabilities, in turn, refer to technological weaknesses that allow attackers to compromise a product and the information it holds. This process needs to be performed continuously in order to keep up with new systems being added to networks, changes that are made to systems, and the discovery of new vulnerabilities over time.__&quot;_

A [vulnerability management](https://www.peerlyst.com/tags/vulnerability-management) [lifecycle](https://www.peerlyst.com/tags/lifecycle) goes through the following six main phases:

- **Identification and discovery** : During this phase, [information security professional](https://www.peerlyst.com/tags/information-security-professional) tries to identify all the [assets](https://www.peerlyst.com/tags/assets) within the discussed scope, including open [services](https://www.peerlyst.com/tags/services) and [operating systems](https://www.peerlyst.com/tags/operating-systems) and tries to [detect](https://www.peerlyst.com/tags/detect) common potential vulnerabilities in an [information system](https://www.peerlyst.com/tags/information-system), usually using [automation](https://www.peerlyst.com/tags/automation) [tools](https://www.peerlyst.com/tags/tools) and vulnerability scanners. Some of the most used [Vulnerability scanners](https://www.peerlyst.com/tags/vulnerability-scanners)are:
  - The discussed scanner &quot;OpenVAS&quot;
  - Nexpose [Community](https://www.peerlyst.com/tags/community)
  - [Nikto](https://www.peerlyst.com/tags/nikto)
  - [Nessus](https://www.peerlyst.com/tags/nessus) Professional
  - [Microsoft](https://www.peerlyst.com/tags/microsoft) [Baseline](https://www.peerlyst.com/tags/baseline) Security Analyzer (MBSA) ( &quot;_This is an area that is probably as a big a__ _[_risk_](https://www.peerlyst.com/tags/risk)_ __as__ _[_vulnerabilities_](https://www.peerlyst.com/tags/vulnerabilities)_ __in software&quot; )_
  - [Comodo](https://www.peerlyst.com/tags/comodo) HackerProof

Note: It is recommended to use more than one [Vulnerability scanner](https://www.peerlyst.com/tags/vulnerability-scanner)

- **Prioritizing and classification:**  The [penetration tester](https://www.peerlyst.com/tags/penetration-tester) prioritizes the assets based on sensitivity criteria or based on categories. You can also prioritize vulnerabilities using a ranking system, for example, using the Common Vulnerability Scoring System (CVSS) for the Common Vulnerabilities and Exposures (CVE) vulnerabilities. For the classification you can check and visit the following helpful websites:
  -
#### [Common Vulnerability Scoring System (CVSS)](https://www.first.org/cvss/)
  -
#### [NVD - Vulnerability Metrics](https://nvd.nist.gov/vuln-metrics/cvss)
  -
#### [CVSS Scores: A Useful Guide - Recorded Future](https://www.recordedfuture.com/cvss-scores-guide/)
- **Assessment:****  **This involves documenting analyzed risks. The [pentester](https://www.peerlyst.com/tags/pentester) must make a decision about the [risk acceptance](https://www.peerlyst.com/tags/risk-acceptance) after an evaluation process. When conducting a vulnerability assessment, you need to validate every found vulnerability. Using vulnerability [scanners](https://www.peerlyst.com/tags/scanners) is important to detect potential vulnerabilities, but penetration testers need to verify every one of them to avoid [false positive](https://www.peerlyst.com/tags/false-positive) and incorrect flags.
- **Report:**  During this phase, [information security](https://www.peerlyst.com/tags/information-security) professional shows the results of the conducted vulnerability assessment including the number of issues and [trends](https://www.peerlyst.com/tags/trends), accompanied by graphical representations of the obtained artefacts.
- **Remediate:**  This is a detailed roadmap that includes recommendations and the steps required to [remediate](https://www.peerlyst.com/tags/remediate) and fix vulnerabilities, not only technically, but it could include budgets, time slots, raking, and so on.
- **Verification** : The final step involves verifying the fixed vulnerabilities after a follow-up check:

To ensure that you are effectively managing vulnerabilities you need to avoid the misconceptions discussed in the last section.

## Vulnerability Management Policy

[Policies](https://www.peerlyst.com/tags/policies) are written documents by high-management level members that specify the responsibilities and required [behaviour](https://www.peerlyst.com/tags/behaviour) of every individual in an organization. In general, policies are short and don&#39;t specify technical aspects, such as [operating](https://www.peerlyst.com/tags/operating) [systems](https://www.peerlyst.com/tags/systems) and vendors. If the organization is large, policies could be divided into sub-policies.

## References:

- [How to establish a good vulnerability management program](https://www.peerlyst.com/posts/how-to-establish-a-good-vulnerability-management-program-chiheb-chebbi?trk=search_page_search_result) by Chiheb Chebbi
