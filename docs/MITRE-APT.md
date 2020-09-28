# Using MITRE ATT&CK to defend against Advanced Persistent Threats

Nowadays, new techniques are invented on a daily basis to bypass security layers and avoid detection. Thus it is time to figure out new techniques too and defend against cyber threats.

![](https://base.imgix.net/files/base/ebm/tdworld/image/2019/04/tdworld_13685_cyberattack_matejmo.png?auto=format&amp;fit=crop&amp;h=432&amp;w=768)

_Image _[_Courtesy_](https://base.imgix.net/files/base/ebm/tdworld/image/2019/04/tdworld_13685_cyberattack_matejmo.png?auto=format&amp;fit=crop&amp;h=432&amp;w=768)

Before diving into how to use MITRE ATT&amp;CK framework to defend against advanced persistent threats and protect critical assets, let&#39;s explore some important terminologies

##  Threats 


By definition, a  **threat**  is a potential danger for the enterprise assets that could harm these systems. In many cases, there is confusion between the three terms Threat, Vulnerability and Risk; the first term, as I explained before, is a potential danger while a Vulnerability is a known weakness or a gap in an asset. A risk is a result of a threat exploiting a vulnerability. In other words, you can see it as an intersection between the two previous terms. The method used to attack an asset is called a  **Threat Vector**.

## Advanced Persistent Threats 

Wikipedia defines an &quot;Advanced Persistence Threat&quot; as follows:

> "An advanced persistent threat is a stealthy computer network threat actor, typically a nation-state or state-sponsored group, which gains unauthorized access to a computer network and remains undetected for an extended period"

To discover some of the well-known APT groups you can check this great resource from FireEye: [Advanced Persistent Threat Groups](https://www.fireeye.com/current-threats/apt-groups.html)

![](https://lh4.googleusercontent.com/TCVMwDJMikRxMYcpfTntHg-M0FVI6ywuriDY6bfRP80NhoE88Mmv_t6T6fXFOBPxnwTe7ooGyb8hvVSxdmBCNnPPfbbgEws_tZDqRrZpz95p_vh5sOOvgvKdq1mPCxUoprgz6ik)

![](https://lh6.googleusercontent.com/ZThxerykAyaiXocODKqI8QEGo3m05SOHSZIbOdV1j3Rz4wnUVQTkrP6eHjmn0DgXEv5f0Ed249mR-Hxci3_hKQN5g52tL2CnNg7bXkATMr6qf7ERSPK5ribQ0N1xUo8L484KGBA)

##  The Cyber Kill Chain 

The Cyber Kill Chain is a military inspired model to describe the required steps and stages to perform attacks. The Cyber Kill Chain framework is created by Lockheed Martin as part of the Intelligence Driven Defense model for identification and prevention of cyber intrusions activity. While a kill chain in military refers to: Find, Fix, Track, Target, Engage and Assess, cyber kill chain refers to: reconnaissance, Initial attack, Command and control, Discover and spread and finally Extraction and exfiltration. Knowing this framework is essential to have a clearer understanding about how major attacks occur.

![](http://www.go4hosting.com/image/blog/AttivoNetworks_KillChain2.png)

_Image _[_Courtesy_](http://www.go4hosting.com/image/blog/AttivoNetworks_KillChain2.png)

Threat intelligence is an important operation in cyber-security and especially in security operations and incident response. Because as Sun Tzu said:

![](https://www.fortinet.com/content/dam/fortinet-blog/article-images/individual-images/AbqKCT0.jpg)

_Image _[_Courtesy_](https://www.fortinet.com/content/dam/fortinet-blog/article-images/individual-images/AbqKCT0.jpg)

Security operation analysts should be proactive when it comes to gathering information and intelligence about the external threats and adversaries to achieve faster detection.

##  MITRE ATT&amp;CK Framework 

<img src="https://lh4.googleusercontent.com/2Hkbqi1hUwm1O8Gyx1xSR8k6E-bWDW_BPBLZbUAAiy6-tzJRk29mm8Af1ByvJIwQQco17ae-2-Ie8Ud3nX4kjv6Tr0rZPQbNHYRGv76c1iIiH-Shh6V7or399uB-buLB2m1PLco" width="200px">


MITRE ATT&amp;CK is a framework developed by the Mitre Corporation. The comprehensive document classifies adversary attacks, in other words, their techniques and tactics after observing millions of real-world attacks against many different organizations. This is why ATT&amp;CK refers to &quot;Adversarial Tactics, Techniques &amp; Common Knowledge&quot;.

Nowadays the frameworks provide different matrices: [Enterprise](https://attack.mitre.org/matrices/enterprise/), [Mobile](https://attack.mitre.org/matrices/mobile/), and [PRE-ATT&amp;CK](https://attack.mitre.org/matrices/pre/). Each matrix contains different tactics and each tactic has many techniques.

But wait, what is a  **tactic**  and what is a  **technique**?

To understand tactics and techniques we need to understand the pyramid of pain first. The pyramid of pain shows the relationship between the types of indicators found when dealing with adversaries. By indicators, I mean Hash values, IP addresses, Domain names, Network/host artefacts, tools and Tactics, techniques and procedures (TTPs).

![](https://lh4.googleusercontent.com/vkdAp0IBNu27mZVCzZTtbUEGMflHiIVbM7qHq4NWeQ5QWnjFdq8yDM0WVm4W7e3_vo-v_tWv1FzUDNivAaSQk9lQg2RZCjQp_IhnsmAVh6fe7k97LY2KHTAxoaRVJvgMXbT661c)

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

![](https://lh6.googleusercontent.com/HbXY-BR_PcfCpqgAfMZVyK4-a1Gmt2sv7zFWRUKmASm9IWUHDVsqeHSnp2V6xtBWNaxQ2S9EpS8KzBGKBhrB8Xml1xDqHpDMnbms3IfZHHyslRwE8_K52mxmXSI1x9tatH9w0hI)

Let&#39;s suppose that security analysts receive a report about a new APT group that threats middle east and Africa. We can take &quot;[Muddy Water](https://www.bankinfosecurity.com/muddywater-apt-group-upgrades-tactics-to-avoid-detection-a-12504) APT&quot; as an example.

Go to [https://mitre-attack.github.io/attack-navigator/enterprise/#](https://mitre-attack.github.io/attack-navigator/enterprise/)

And highlight all the techniques used by Muddy Water APT Group

![](https://lh5.googleusercontent.com/8MwNDmK4mPniKa0L_Bzh37MkmJmcwJLPKkFsv8YtZTwU13kXZI2P9vARfpC9bhmYSmB5g8XdbP6407H93UKEQMoqa_xseHr5ml-RPBNPiKfPAvaidYElVrbuonn9RYuLIz1dA4I)

Export the techniques as SVG

![](https://lh4.googleusercontent.com/Lg7XC7BfAM6SBNbOummMk2Q4o5Kvp-8FXchWxg_Wxgiqj3aj8l1QLdM6tRTGqj8Wgivo-mQrXifqOGVJi4JvEkHkCsQB62jhRJwrtC_xG1fOd6XoO_OkyNTirII0YbDJf_vqooE)

If you are dealing with many APT groups at the same time highlight the techniques using colorful shades depends on how often the technique is used by the APT groups (brightest color = The technique is used by many groups)

<img src="https://www.schemecolor.com/wp-content/uploads/lunar-eclipses-red-colors.png" width="200px">

_Image _[_Courtesy_](https://www.schemecolor.com/wp-content/uploads/lunar-eclipses-red-colors.png)_ _

Now you know your adversaries. It is time to prepare the mitigations (tools and techniques) and discover the gaps in our defenses.

Create a roadmap to improve the defense gaps and update the map accordingly

![](https://lh3.googleusercontent.com/3zW4UI0EASdSGA5Mzjsj29-ArGsfpEyh-rDPMR1mUCUtOFAQ6mtPTdKbqXreY-sxXbNXQZaXbI49VktueIAX-U-4mLYCJRHysN1BjGcDUfGdcOnxo6KAEpwLkCoxEysooYpN-ZI)

Mitigations for every technique can be found on [https://attack.mitre.org/mitigations/enterprise/](https://attack.mitre.org/mitigations/enterprise/)

![](https://lh6.googleusercontent.com/GU6CPDE1UTMYuFtw6XSuMJg-bu1D4NyE5eBO5X4KPPuGBCQzf6R-aCQDVUbB9pqJIdR6w9G0xOaZCxCIvPlmRkcObjkcOXVDXCHqvZuO9ovl-jZtcByHNRaP-od0mVoD25wtAek)


##   Summary

In this module, we learned many important terminologies and how to use MITRE ATT&amp;CK framework to detect advanced persistent threats.


### References  

- [https://www.fireeye.com/blog/products-and-services/2020/01/operationalizing-cti-hunt-for-defend-against-iranian-cyber-threats.html](https://www.fireeye.com/blog/products-and-services/2020/01/operationalizing-cti-hunt-for-defend-against-iranian-cyber-threats.html)



