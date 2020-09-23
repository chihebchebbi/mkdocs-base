# Incident Response and Security Operations Fundamentals

In this module, we are going to discover the required terminologies and fundamentals to acquire a fair understanding of “Incident Response” and the different steps and teams to perform incident response

We are going to explore the following points: 

*	Attack Vector Analysis
* Incident Response Fundamentals 
*	Incident Response Standards and Guidelines
*	Incident response Process
*	Incident response Teams
*	Security Operation Centers

Before exploring what incident response is, let’s explore some important terminologies

Attack vector analysis 
Attack vectors are the paths used by attackers to access a vulnerability. In other words, the method used to attack an asset is called a Threat Vector or Attack vector. Attack vectors can be analyzed. The analysis is done by studying the attack surfaces like the entry points of an application, APIs, files, databases, user interfaces and so on. When you face a huge number of entries you can divide the modeling into different categories (APIs, Business workflows etc...)
 
![](https://eforensicsmag.com/wp-content/uploads/2014/12/Untitled.png)

## Incident Response Fundamentals 

TechTarget defines incident response as follows: 
“Incident response is an organized approach to addressing and managing the aftermath of a security breach or cyberattack, also known as an IT incident, computer incident or security incident. The goal is to handle the situation in a way that limits damage and reduces recovery time and costs.”

But what is an information security Incident?

An event is any observable occurrence in a system or network. Events include a user connecting to a file share, a server receiving a request for a web page, a user sending email, and a firewall blocking a connection attempt. Incidents are events with a negative consequence, such as system crashes, packet floods, unauthorized use of system privileges, unauthorized access to sensitive data, and execution of malware that destroys data.
During incident response operation there are a lot of artifacts resources you need to collect. You can use different artifacts such as: 

*	IP addresses
*	Domain names
*	URLs
*	System calls
*	Processes
*	Services and ports
*	File hashes


## Incident Response Process

Incident response like any methodological operation goes thru a well-defined number of steps:

1.	Preparation: during this phase, the teams deploy the required tools and resources to successfully handle the incidents including developing awareness training.
2.	Detection and analysis: this is the most difficult phase. It is a challenging step for every incident response team. This phase includes networks and systems profiling, log retention policy, signs of an incident recognition and prioritizing security incidents.
3. Containment eradication and recovery: during this phase, the evidence pieces are collected and the containment and recovery strategies are maintained.
4. 	Post-incident activity: discussions are held during this phase to evaluate the team performance, to determine what actually happened, policies compliance and so on.
 
![](https://www.exabeam.com/wp-content/uploads/2018/09/IR-plan-steps.png)

## Establishing incident response teams

There are different incident response Teams: 
*	Computer Security Incident Response Teams
*	Product Security Incident Response Teams 
*	National CSIRTs and Computer Emergency Response Team.
 
![](https://letsaskme.com/wp-content/uploads/2019/11/noc.png)

## Incident response standards and guidelines: 
There are many great standards and guidelines to help you become more resilient and help you to build a mature incident response program some of the following: 
* Computer Security Incident Handling Guide: (NIST 800-63  Second revision),  you can find it here: Computer Security Incident Handling Guide - NIST Page  
*	ISO 27035: ISO/IEC 27035 Security incident management 
*	SANS Incident Handler Handbook: Incident Handler's Handbook - SANS.org
* CREST Cyber Security Incident Response Guide: Cyber Security Incident Response Guide - crest

## Security Operation Centers Fundamentals

Wikipedia defines Security Operation Centers as follows: 
A security operations center is a centralized unit that deals with security issues on an organizational and technical level. A SOC within a building or facility is a central location from where staff supervises the site, using data processing technology.
 
![](https://www.xiarch.com/assets/images/services/soc-solutions.png)

Security Operation Centers are not only a collection of technical tools. SOCs are people, process and technology. 

To help you prepare your mission I highly recommend you to read this guide from  Sampson Chandler : Incident Response Guide


It is essential to evaluate your SOC maturity because you can’t improve what you cannot measure. There are many maturity models in the wild based on different metrics based on your business needs and use cases. 
Some of the metrics are: 
* Time to Detect (TTD)
* Time to Respond (TDR)
 
![](https://res.cloudinary.com/logrhythm/image/upload/c_scale,w_800/v1550260288/blog-images/2019-Q1/a-CTOs-take-on-the-security-operations-maturity-model-image-2.png)

Your maturity model will be identified using this graph from LogRythm: 
 
![](https://res.cloudinary.com/logrhythm/image/upload/c_scale,w_800/v1550260288/blog-images/2019-Q1/a-CTOs-take-on-the-security-operations-maturity-model-image-4.png)

## Summary
By now I assume that we covered many important terminologies and steps to perform incident response. The major goal of writing this article is delivering a collaborated guide to help our readers learning the fundamental skills needed in a daily basis job as incident handlers. 
Your comments are playing a huge role in this article. Please if you want to add or correct something please don’t hesitate to comment so we can create together a one-stop resource for readers who are looking for a guide to learn about Incident Response. All your comments are welcome!

## References and Credit
1.	https://searchsecurity.techtarget.com/definition/incident-response 
2.	https://logrhythm.com/blog/a-ctos-take-on-the-security-operations-maturity-model/ 
