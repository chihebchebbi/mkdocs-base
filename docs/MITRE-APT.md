# Using MITRE ATT&CK to defend against Advanced Persistent Threats


Nowadays, new techniques are invented on a daily basis to bypass security layers and avoid detection. Thus it is time to figure out new techniques too and defend against cyber threats.

![](https://base.imgix.net/files/base/ebm/tdworld/image/2019/04/tdworld_13685_cyberattack_matejmo.png?auto=format&amp;fit=crop&amp;h=432&amp;w=768)

_Image _[_Courtesy_](https://base.imgix.net/files/base/ebm/tdworld/image/2019/04/tdworld_13685_cyberattack_matejmo.png?auto=format&amp;fit=crop&amp;h=432&amp;w=768)

Before diving into how to use MITRE ATT&amp;CK framework to defend against advanced persistent threats and protect critical assets, let&#39;s explore some important terminologies

## **Threats **

![](https://wpsitehelpers.com/wp-content/uploads/2016/11/wordpress-malware-removal.png)

_Image _[_Courtesy_](https://wpsitehelpers.com/wp-content/uploads/2016/11/wordpress-malware-removal.png)

By definition, a  **threat**  is a potential danger for the enterprise assets that could harm these systems. In many cases, there is confusion between the three terms Threat, Vulnerability and Risk; the first term, as I explained before, is a potential danger while a Vulnerability is a known weakness or a gap in an asset. A risk is a result of a threat exploiting a vulnerability. In other words, you can see it as an intersection between the two previous terms. The method used to attack an asset is called a  **Threat Vector**.

## **Advanced Persistent Threats**

Wikipedia defines an &quot;Advanced Persistence Threat&quot; as follows:

_&quot;An  __advanced persistent threat__  is a stealthy computer  __network__   __threat actor__ , typically a nation-state or state-sponsored group, which gains  __unauthorized access__  to a computer network and remains undetected for an extended period&quot;_

To discover some of the well-known APT groups you can check this great resource from FireEye: [Advanced Persistent Threat Groups](https://www.fireeye.com/current-threats/apt-groups.html)

![](RackMultipart20200923-4-16yksxn_html_5128e66636a3133f.png)

![](RackMultipart20200923-4-16yksxn_html_637f115c4eb01d.png)

## **The Cyber Kill Chain**

The Cyber Kill Chain is a military inspired model to describe the required steps and stages to perform attacks. The Cyber Kill Chain framework is created by Lockheed Martin as part of the Intelligence Driven Defense model for identification and prevention of cyber intrusions activity. While a kill chain in military refers to: Find, Fix, Track, Target, Engage and Assess, cyber kill chain refers to: reconnaissance, Initial attack, Command and control, Discover and spread and finally Extraction and exfiltration. Knowing this framework is essential to have a clearer understanding about how major attacks occur.

![](http://www.go4hosting.com/image/blog/AttivoNetworks_KillChain2.png)

_Image _[_Courtesy_](http://www.go4hosting.com/image/blog/AttivoNetworks_KillChain2.png)

Threat intelligence is an important operation in cyber-security and especially in security operations and incident response. Because as Sun Tzu said:

![](https://www.fortinet.com/content/dam/fortinet-blog/article-images/individual-images/AbqKCT0.jpg)

_Image _[_Courtesy_](https://www.fortinet.com/content/dam/fortinet-blog/article-images/individual-images/AbqKCT0.jpg)

Security operation analysts should be proactive when it comes to gathering information and intelligence about the external threats and adversaries to achieve faster detection.

## **MITRE ATT&amp;CK Framework**

![](RackMultipart20200923-4-16yksxn_html_a1f3903ce3b17ff4.png)

MITRE ATT&amp;CK is a framework developed by the Mitre Corporation. The comprehensive document classifies adversary attacks, in other words, their techniques and tactics after observing millions of real-world attacks against many different organizations. This is why ATT&amp;CK refers to &quot;Adversarial Tactics, Techniques &amp; Common Knowledge&quot;.

Nowadays the frameworks provide different matrices: [Enterprise](https://attack.mitre.org/matrices/enterprise/), [Mobile](https://attack.mitre.org/matrices/mobile/), and [PRE-ATT&amp;CK](https://attack.mitre.org/matrices/pre/). Each matrix contains different tactics and each tactic has many techniques.

But wait, what is a  **tactic**  and what is a  **technique**?

To understand tactics and techniques we need to understand the pyramid of pain first. The pyramid of pain shows the relationship between the types of indicators found when dealing with adversaries. By indicators, I mean Hash values, IP addresses, Domain names, Network/host artefacts, tools and Tactics, techniques and procedures (TTPs).

![](RackMultipart20200923-4-16yksxn_html_5fbc4555ec472a8b.png)

_Image _[_Courtesy_](http://3.bp.blogspot.com/-rZkSSNqMxqA/Wvq-rMvj2FI/AAAAAAAAMkk/fgnVNRBrdnwrgF_bWy0iDi7HJ-nqLxg7QCLcBGAs/s640/Screen%2BShot%2B2018-05-15%2Bat%2B1.02.42%2BPM.png)

Tactics, Techniques and procedures (TTPs) are how the attackers are going to achieve their mission. A tactic is the highest level of attack behaviour. MITRE framework present the tactics as the following:

1. **Initial Access**
2. **Execution**
3. **Persistence**
4. **Privilege Escalation**
5. **Defense Evasion**
6. **Credential Access**
7. **Discovery**
8. **Lateral Movement**
9. **Collection**
10. **Exfiltration**
11. **Command and Control**

Techniques are used to execute an attack successfully. For example, this is information about the &quot;_AppCertDLLs_&quot; technique

![](RackMultipart20200923-4-16yksxn_html_3328c8a8f03042f2.png)

Let&#39;s suppose that security analysts receive a report about a new APT group that threats middle east and Africa. We can take &quot;[Muddy Water](https://www.bankinfosecurity.com/muddywater-apt-group-upgrades-tactics-to-avoid-detection-a-12504) APT&quot; as an example.

Go to [https://mitre-attack.github.io/attack-navigator/enterprise/#](https://mitre-attack.github.io/attack-navigator/enterprise/)

And highlight all the techniques used by Muddy Water APT Group

![](RackMultipart20200923-4-16yksxn_html_5bca1bd32be12882.png)

Export the techniques as SVG

![](RackMultipart20200923-4-16yksxn_html_ce015078badae193.png)

If you are dealing with many APT groups at the same time highlight the techniques using colorful shades depends on how often the technique is used by the APT groups (brightest color = The technique is used by many groups)

![](https://www.schemecolor.com/wp-content/uploads/lunar-eclipses-red-colors.png)

_Image _[_Courtesy_](https://www.schemecolor.com/wp-content/uploads/lunar-eclipses-red-colors.png)_ _

Now you know your adversaries. It is time to prepare the mitigations (tools and techniques) and discover the gaps in our defenses.

Create a roadmap to improve the defense gaps and update the map accordingly

![](RackMultipart20200923-4-16yksxn_html_565dd6c3a94ee053.png)

Mitigations for every technique can be found on [https://attack.mitre.org/mitigations/enterprise/](https://attack.mitre.org/mitigations/enterprise/)

![](RackMultipart20200923-4-16yksxn_html_ed02c2f56802bed8.png)

## **Threat Emulation**

One of the techniques to help you practice how to defend your organization from these attacks is Threat Emulation. You can use Atomic Red Team to train your team.

![](RackMultipart20200923-4-16yksxn_html_8e6b3fb35333cc8d.png)

_&quot;_[_Atomic Red Team_](https://atomicredteam.io/)_ is a library of simple  __tests__  that every  __security team__  can execute to test their defenses. Tests are focused, have few dependencies, and are defined in a structured  __format__  that can be used by  __automation__  frameworks.&quot;_



## **Summary**

In this article, we learned many important terminologies and how to use MITRE ATT&amp;CK framework to detect advanced persistent threats.


**References and Credit**

- [https://www.fireeye.com/blog/products-and-services/2020/01/operationalizing-cti-hunt-for-defend-against-iranian-cyber-threats.html](https://www.fireeye.com/blog/products-and-services/2020/01/operationalizing-cti-hunt-for-defend-against-iranian-cyber-threats.html)


