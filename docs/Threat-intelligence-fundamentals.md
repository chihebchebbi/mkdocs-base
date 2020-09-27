# Threat Intelligence Fundamentals

### What is a threat? 
By definition, a threat is a potential danger for the enterprise assets that could harm these systems. In many cases, there is confusion between the three terms Threat, Vulnerability and Risk; the first term, as I explained before, is a potential danger while a Vulnerability is a known weakness or a gap in an asset. A risk is a result of a threat exploiting a vulnerability. In other words, you can see it as an intersection between the two previous terms. The method used to attack an asset is called a Threat Vector.


There are three main types of threats:
*	Natural threats 
*	Unintentional threats 
*	Intentional threats

### What is an advanced Persistent Threat (APT)? 
Wikipedia defines an "Advanced Persistent Threat" as follows:

> "An advanced persistent threat is a stealthy computer network threat actor, typically a nation-state or state-sponsored group, which gains unauthorized access to a computer network and remains undetected for an extended period"

![GitHub Logo](https://images.idgesg.net/images/article/2018/02/security_threats_hackers_malware_spyware_phishing_virus_thinkstock_905222206-100749995-large.jpg)

To explore some APTs Check this great resource by: FireEye

### What is Threat Intelligence? 

> “Cyber threat intelligence is information about threats and threat actors that helps mitigate harmful events in cyberspace. Cyber threat intelligence sources include open source intelligence, social media intelligence, human Intelligence, technical intelligence or intelligence from the deep and dark web "[Source: Wikipedia]

In other words, intelligence differs from data and information as completing the full picture. 

Threat Intelligence goes through the following steps: 

1.	Planning and direction 
2.	Collection
3.	Processing and exploitation
4.	Analysis and production
5.	Dissemination and integration 

![GitHub Logo](https://miro.medium.com/max/500/1*GinpKSzxpyPGUgbUz9E1ZQ.png)
 
### What are the Indicators of compromise (IOCs)?

Indicators of compromise are pieces of information about a threat that can be used to detect intrusions such as MD5 hashed, URLs, IP addresses and so on.
 
These pieces can be shared accross different organizations thanks to bodies like: 
*	Information Sharing and Analysis Centers (ISACs)
*	Computers emergency response teams (CERTs)
*	Malware Information Sharing Platform (MISP)

To facilitate the sharing/collecting/analyzing processes these IOCs usually respect and follow certain formats and protocols such as: 

*	OpenIOC
*	Structured Threat Information eXpression (STIX)
*	Trusted Automated Exchange of Intelligence Information (TAXII)

For example, this is the IOC STIX representation of Wannacry ransomware:

![GitHub Logo](https://www.researchgate.net/profile/Ashwinkumar_Ganesan/publication/329064578/figure/fig2/AS:703195873542144@1544666369406/STIX-representation-of-Wannacry-Ransomware.ppm)

To help you create and edit your indicators of compromise you can use, for rxample, IOC editor by Fireeye. You can find it here: 
This is its user guide:

You can simply create your Indicators of compromise using a graphical interface: 

![GitHub Logo](https://windows-cdn.softpedia.com/screenshots/IOCe_1.png)
 
 It gives you also the ability to compare IOCs

