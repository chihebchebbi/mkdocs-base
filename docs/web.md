# **How to attack and secure Web Applications Guide**

## How to attack and secure Web Applications Guide

![](RackMultipart20200926-4-i1kaba_html_781da84c1f60896a.jpg)_source:__ _[_https://www.qualys.com/asset/image/web-application-security-600-2x.jpg_](https://www.qualys.com/asset/image/web-application-security-600-2x.jpg)

**Abstract****  **

Hi Peerlysters! Web applications are undoubtedly playing a huge role in our daily activities from sharing photos of cute cats to handling millions of business activities every second. Thus, making sure that they are secure is a must. This article will give you the core skills and [techniques](https://www.peerlyst.com/tags/techniques) you need to effectively conduct web application [penetration tests](https://www.peerlyst.com/tags/penetration-tests) and evaluate them. We will start by discussing important terminologies and attacks and finally, we will explore the [OWASP TOP 10](https://www.peerlyst.com/tags/owasp-top-10) Web app threats.

In this Article we are going to discover:

- **Web Application Overview****  **
- **HTTP Headers**
- **Cross-site scripting**
- **SQL Injection**
- **NoSQL Injection**
- **Local file inclusion**
- **Remote file inclusion**
- **Cross-Site Request Forgery (CSRF)**** **
- **Web Application Firewalls (WAFs)**
- **Web Vulnerability Scanners**
- **Web Application Security Guidelines**

This article will contain also a useful document where you can find many Proof of concepts (PoCs) of many web application attacks. You can [download](https://www.peerlyst.com/tags/download) it from here: [Web Application security PoCs and writeups](https://static.peerlyst.com/image/upload/v1534793658/post-attachments/Web_Application_security_PoCs_and_writeups_kfkzdy.pdf)

**Note: \*\*****  **This article will be updated with more web application attacks \*\* in the next days

## Web Application Overview

Before diving deep into [how to](https://www.peerlyst.com/tags/how-to) attack and secure Web Applications, we need to dissect what web applications really are. An application by definition is a program that performs specific tasks. We are using many applications on a daily basis like eBooks readers, Trading platforms, emailing applications and so on. [Web applications](https://searchsoftwarequality.techtarget.com/definition/Web-application-Web-app) are stored on a remote server and delivered over the [Internet](https://www.peerlyst.com/tags/internet)through a browser interface.

Web applications are developed based on many different architectures. The following is a simple example of them.

![](RackMultipart20200926-4-i1kaba_html_2246e02d4dcf5098.png)

_Source:__ _[_http://www.eitdigital.com/images/appnetwork-small.gif_](http://www.eitdigital.com/images/appnetwork-small.gif)

## HTTP Headers

[HTTP Headers](https://www.peerlyst.com/tags/http-headers) are allowing the [exchange](https://www.peerlyst.com/tags/exchange-2014) of information between Generally we have 4 types of [HTTP](https://www.peerlyst.com/tags/http) headers:

- General-header
- Client Request-header
- Server Response-header
- Entity-header

![](RackMultipart20200926-4-i1kaba_html_e0d9a5a9a3bdb26d.png)

_Source:__ _[_https://cdn.tutsplus.com/net/uploads/legacy/511\_http/http\_diagram.png_](https://cdn.tutsplus.com/net/uploads/legacy/511_http/http_diagram.png)

The analyse HTTP Headers you can use [Firebug](https://www.peerlyst.com/tags/firebug) extension:

![](RackMultipart20200926-4-i1kaba_html_509639bc8574532a.png)

_Source:__ _[_https://cdn.tutsplus.com/net/uploads/legacy/511\_http/firebug.png_](https://cdn.tutsplus.com/net/uploads/legacy/511_http/firebug.png)

To learn more about HTTP headers I highly recommend you to read this great Peerlyst Post from Brad Voris: **[HTTP Headers for the Security Professional](https://www.peerlyst.com/posts/http-headers-for-the-security-professional-brad-voris?trk=search_page_search_result)****, ****  ** where he explained in a detailed way the different HTTP Headers

## Web Application Attacks

![](RackMultipart20200926-4-i1kaba_html_9ee88df06b4f2c00.png)

_source:__ _[_https://www.hs-academypages.com/hubfs/lp/academy/xss.png?t=1533671812486_](https://www.hs-academypages.com/hubfs/lp/academy/xss.png?t=1533671812486)

By now, we discovered some important terminologies in web applications. Let&#39;s explore some of the most well-known web application attacks and vulnerabilities. There many web attacks but we are going to only explore some of them.

## XSS (Cross-site scripting)

In [Cross-site scripting](https://www.peerlyst.com/tags/cross-site-scripting-1) (XSS) attacks the criminal can inject [malicious](https://www.peerlyst.com/tags/malicious) [scripts](https://www.peerlyst.com/tags/scripts) into the web application which help him bypass restriction, [steal](https://www.peerlyst.com/tags/steal) [credentials](https://www.peerlyst.com/tags/credentials), [Hijack](https://www.peerlyst.com/tags/hijack) [sessions](https://www.peerlyst.com/tags/sessions), and many other malicious activities. If you want to test if a web page is vulnerable to [XSS attacks](https://www.peerlyst.com/tags/xss-attacks), for example, find an input field and print anything like &quot;This is a Test&quot;. If it appears on the webpage then the page is vulnerable. Another case, insert

This graph illustrates how the Attacker can [Exploit](https://www.peerlyst.com/tags/exploit) [Cross-site scripting](https://www.peerlyst.com/tags/cross-site-scripting-1) (XSS) vulnerability:

![](RackMultipart20200926-4-i1kaba_html_d502f4b0a2ecd661.png)

_source:__ _[_https://dejanstojanovic.net/media/215060/xss.png_](https://dejanstojanovic.net/media/215060/xss.png)

Cross-site [scripting](https://www.peerlyst.com/tags/scripting) (XSS) attacks categories are:

- **Persistent XSS** , where the malicious input originates from the website&#39;s database.
- **Reflected XSS** , where the malicious input originates from the victim&#39;s request.
- **DOM-based XSS** , where the [vulnerability](https://www.peerlyst.com/tags/vulnerability) is in the client-side code rather than the server-side code. ( [https://excess-xss.com/](https://excess-xss.com/))

## SQL Injection

This is a server-side attack that takes advantage of [vulnerabilities](https://www.peerlyst.com/tags/vulnerabilities) in web applications to send [unauthorized](https://www.peerlyst.com/tags/unauthorized) [database](https://www.peerlyst.com/tags/database) queries. During this web attack, the attacker extracts [sensitive information](https://www.peerlyst.com/tags/sensitive-information) like [passwords](https://www.peerlyst.com/tags/passwords) and business data by [manipulating](https://www.peerlyst.com/tags/manipulating) the data to cause their own database query to execute, allowing them to read or modify the contents of the database

![](RackMultipart20200926-4-i1kaba_html_7fad7c6a9a1fd0f6.png)

_Source:__ _[_https://www.guru99.com/images/EthicalHacking/Article\_13\_7.png_](https://www.guru99.com/images/EthicalHacking/Article_13_7.png)

There are many [SQL injection attack](https://www.peerlyst.com/tags/sql-injection-attack) categories:

- **Error-Based SQL injection**
- **Union-Based SQL injection**
-
### Blind SQL injection:


  -
### Time-based SQLi
  -
### Boolean-based SQLi

To learn more about [SQL injection](https://www.peerlyst.com/tags/sql-injection) you can check these great Peerlyst resources:

-
### [**SQL Injections – Part 1**](https://www.peerlyst.com/posts/sql-injections-part-1-hari-charan?trk=search_page_search_result)
-
### [**SQL Injections and Countermeasures**](https://www.peerlyst.com/posts/sql-injections-and-countermeasures-hari-charan?trk=search_page_search_result)
-
### [**Tips for an Information Security Analyst/Pentester career - Episode 9: DVWA (SQL injection)**](https://www.peerlyst.com/posts/tips-for-an-information-security-analyst-pentester-career-episode-9-dvwa-sql-injection-mattia-campagnano-13-years-experience-akron-oh?trk=search_page_search_result)
-
### [**5 minutes explanation of SQL injections and recommended solutions**](https://www.peerlyst.com/posts/5-minutes-explanation-of-sql-injections-and-recommended-solutions-dawid-balut?trk=search_page_search_result)

## NoSQL Injection

NoSQL is an approach to database design that can accommodate a wide variety of data models, including key-value, document, columnar and graph formats. NoSQL, which stands for &quot;not only SQL,&quot; is an alternative to traditional relational databases in which data is placed in tables and data schema is carefully designed before the [database](https://www.peerlyst.com/tags/database) is built. NoSQL databases are especially useful for working with large sets of distributed data [Source: [https://searchdatamanagement.techtarget](https://searchdatamanagement.techtarget/) ]

Non-relational databases can be categorized into 4 major categories:

- **Document-oriented**
- **Column Family**
- **Key value stores**
- **Graph databases.**

One of the biggest [threats](https://www.peerlyst.com/tags/threats) to NoSQL is &quot;NoSQL injection&quot;. [Malicious](https://www.peerlyst.com/tags/malicious) inputs could be a huge problem even we are no longer dealing with the query language. In this small Demonstration done by [Pete Corey](http://www.petecorey.com/blog/2017/07/03/what-is-nosql-injection/) He delivered a short [vulnerable](https://www.peerlyst.com/tags/vulnerable) [code](https://www.peerlyst.com/tags/code):

![](RackMultipart20200926-4-i1kaba_html_47f58c17e705dc7a.png)

#### Source [https://imgur.com/ssWgBum](https://imgur.com/ssWgBum)

If you type admin as [username](https://www.peerlyst.com/tags/username) and {$gte: &quot;&quot;} as [Password](https://www.peerlyst.com/tags/password) the result query will be the following:

db.users.findOne({ [username](https://www.peerlyst.com/tags/username): &quot;admin&quot;, hashedPassword: {$gte: &quot;&quot;}})

and this query will return the first document it finds with a username of &quot;admin&quot; and a hashed [password](https://www.peerlyst.com/tags/password) that is greater an empty string. The full reading is here: [http://www.petecorey.com/blog/2017/07/03/what-is-nosql-injection/](http://www.petecorey.com/blog/2017/07/03/what-is-nosql-injection/)

[Testing](https://www.peerlyst.com/tags/testing) for NoSQL [injection](https://www.peerlyst.com/tags/injection): [https://www.owasp.org/index.php/Testing\_for\_NoSQL\_injection](https://www.owasp.org/index.php/Testing_for_NoSQL_injection)

These are some [Payload](https://www.peerlyst.com/tags/payload) you can use them for [testing](https://www.peerlyst.com/tags/testing) purposes; [Payloads](https://www.peerlyst.com/tags/payloads) All The Things: [https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/NoSQL%20injection](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/NoSQL%20injection)

To learn more you can check this great presentation:

- [https://www.owasp.org/images/e/ed/GOD16-NOSQL.pdf](https://www.owasp.org/images/e/ed/GOD16-NOSQL.pdf)

To defend against [SQL](https://www.peerlyst.com/tags/sql) / NoSQL Injection [Chetan Karande](https://github.com/ckarande) from [OWASP](https://www.peerlyst.com/tags/owasp) organization suggest the following steps:

- Prepared Statements: For SQL calls, use [prepared statements](https://www.peerlyst.com/tags/prepared-statements) instead of building dynamic queries using string concatenation.
- [Input Validation](https://www.peerlyst.com/tags/input-validation): Validate inputs to detect malicious values. For NoSQL databases, also validate input types against expected types
- Least Privilege: To minimize the potential damage of a successful [injection](https://www.peerlyst.com/tags/injection) attack, do not assign [DBA](https://www.peerlyst.com/tags/dba) or admin type access [rights](https://www.peerlyst.com/tags/rights) to your application accounts. Similarly, minimize the privileges of the [operating system](https://www.peerlyst.com/tags/operating-system) account that the database process runs under.

### **To learn more about NoSQL injection you can read my Peerlyst article:****  **[**How to secure NoSQL**](https://www.peerlyst.com/posts/how-to-secure-nosql-chiheb-chebbi?trk=search_page_search_result)

## LFI (Local file inclusion)

[Local file inclusion](https://www.peerlyst.com/tags/local-file-inclusion) is an attack where the criminal manipulate the web application to include files on the web server (only include local files) because later we are going to explore  **Remote file inclusion****  **where the attacker uses remote files.

You can find many [scanners](https://www.peerlyst.com/tags/scanners) in this Peerlyst Post: [Pentest tools: LFI scanners and exploiters](https://www.peerlyst.com/posts/pentest-tools-lfi-scanners-and-exploiters-karl-m-1?trk=search_page_search_result)

## RFI (Remote file inclusion)

In a [Remote file inclusion](https://www.peerlyst.com/tags/remote-file-inclusion), the attacker [exploits](https://www.peerlyst.com/tags/exploits) a [weakness](https://www.peerlyst.com/tags/weakness) in the web application that dynamically includes external files. If a developer leave inputs without properly sanitizing them will make the attacker easily passing them into file include commands. To defend against Remote file inclusion you need to maintain a _whitelist_ of files that can be included.

## Cross-Site Request Forgery (CSRF)

[Cross-Site Request Forgery](https://www.peerlyst.com/tags/cross-site-request-forgery) is an attack where the attacker needs to be authenticated in order to trick the [victim](https://www.peerlyst.com/tags/victim) to perform malicious activities. This attack can be done by tricking the victim into clicking a specific link via many techniques like [Social engineering](https://www.peerlyst.com/tags/social-engineering)which is a technique to manipulate and exploit the psychological aspects of the target. Finally, the attacker sends a forged request to the victim then the website will validate that request.

## Directory Traversal

In this attack, the attacker tries to access restricted directories. Sometimes this attack is called Path Traversal. Attackers use  **../****   **to go to an upper folder. They can duplicate those symbols until they find the folders. To defend against [Directory traversal](https://www.peerlyst.com/tags/directory-traversal) you need to validate user input from browsers.

## OS Command Injection

In this attack, the attacker, as usual, exploit non-sanitized input fields to insert [operating systems](https://www.peerlyst.com/tags/operating-systems) commands to run them on the server [operating system](https://www.peerlyst.com/tags/operating-system) which make them able to manipulate the files.

## Web Application Firewalls (WAFs)

A web application firewall (WAF) is a security solution that filters out bad HTTP traffic between a client and web application. It is a common [security control](https://www.peerlyst.com/tags/security-control) to help you protect your web application security. Most Web application firewalls are helping you to defend against many of the previously discussed web application vulnerabilities (XSS, [SQLi](https://www.peerlyst.com/tags/sqli) and so on)

![](RackMultipart20200926-4-i1kaba_html_546b543279917ff0.png)

_source: web-application-firewall.png_

They can operate on 2 different modes:

- **A whitelisting model**
- **A blacklisting model****  **

This is a good list of WAFs: ** ** [A List of Open Source Web Application Firewalls (WAF&#39;s)](https://www.peerlyst.com/posts/resource-a-list-of-open-source-web-application-firewalls-waf-s-s-delano?trk=search_page_search_result)

## Web Vulnerability Scanners

To Test the [security posture](https://www.peerlyst.com/tags/security-posture) of web application you can use a wide range of Web app [vulnerability scanners](https://www.peerlyst.com/tags/vulnerability-scanners) like:

- [w3af - Open Source Web Application Security Scanner:](http://w3af.org/)

[w3af](https://www.peerlyst.com/tags/w3af) is a  **Web Application Attack and Audit Framework**. The project&#39;s goal is to create a [framework](https://www.peerlyst.com/tags/framework) to help you secure your web applications by finding and exploiting all web application vulnerabilities.

![](RackMultipart20200926-4-i1kaba_html_4f45a73aaa7a0d2e.png)

_Source:__ _[_http://w3af.org/wp-content/uploads/gui-gtk.png_](http://w3af.org/wp-content/uploads/gui-gtk.png)

The following are also very helpful Web application vulnerability scanners

- [Web vulnerability scanner - PortSwigger](https://portswigger.net/vulnerability-scanner)
- [Detectify: Leading Website Vulnerability Scanner](https://detectify.com/)
- [Acunetix Vulnerability Scanner](https://www.acunetix.com/vulnerability-scanner/)

##

## Web Application Security Guidelines:

Guidance or guidelines are a set of recommended tips and useful pieces of advice from hands-on experienced people and institutions. There are many [standards](https://www.peerlyst.com/tags/standards) and guidelines followed by [penetration](https://www.peerlyst.com/tags/penetration) testers. One of them is the OWASP. According to their official website:

_The__ _[_Open Web Application Security Project_](https://www.peerlyst.com/tags/open-web-application-security-project)_ __(OWASP) is a__ _[_501(c)(3)_](https://www.irs.gov/charities-non-profits/charitable-organizations/exemption-requirements-section-501c3-organizations)_ __worldwide not-for-profit charitable organization focused on improving the security of software. Our mission is to make__ _[_software security_](https://www.peerlyst.com/tags/software-security)_ _[_visible,_](https://www.owasp.org/index.php/Category:OWASP_Video)_ __so that__ _[_individuals and organizations_](https://www.owasp.org/index.php/Industry:Citations)_are able to make informed decisions.__ _[_OWASP_](https://www.peerlyst.com/tags/owasp)_  __is in a unique position to provide impartial, practical information about AppSec to individuals, corporations,__  _[_universities_](https://www.peerlyst.com/tags/universities)_,__ _[_government_](https://www.peerlyst.com/tags/government)_ __agencies and other organizations worldwide.__ _[_Operating_](https://www.peerlyst.com/tags/operating)_ __as a community of like-minded professionals, OWASP issues software tools and knowledge-based__ _[_documentation_](https://www.peerlyst.com/tags/documentation)_ __on application security._

The OWASP [TOP 10](https://www.peerlyst.com/tags/top-10) Web vulnerabilities are the following:

- [**A1:2017-Injection**](https://www.owasp.org/index.php/Top_10-2017_A1-Injection)
- [**A2:2017-Broken Authentication**](https://www.owasp.org/index.php/Top_10-2017_A2-Broken_Authentication)
- [**A3:2017-Sensitive Data Exposure**](https://www.owasp.org/index.php/Top_10-2017_A3-Sensitive_Data_Exposure)
- [**A4:2017-XML External Entities (XXE)**](https://www.owasp.org/index.php/Top_10-2017_A4-XML_External_Entities_(XXE))
- [**A5:2017-Broken Access Control**](https://www.owasp.org/index.php/Top_10-2017_A5-Broken_Access_Control)
- [**A6:2017-Security Misconfiguration**](https://www.owasp.org/index.php/Top_10-2017_A6-Security_Misconfiguration)
- [**A7:2017-Cross-Site Scripting (XSS)**](https://www.owasp.org/index.php/Top_10-2017_A7-Cross-Site_Scripting_(XSS))
- [**A8:2017-Insecure Deserialization**](https://www.owasp.org/index.php/Top_10-2017_A8-Insecure_Deserialization)
- [**A9:2017-Using Components with Known Vulnerabilities**](https://www.owasp.org/index.php/Top_10-2017_A9-Using_Components_with_Known_Vulnerabilities)
- [**A10:2017-Insufficient Logging&amp;Monitoring**](https://www.owasp.org/index.php/Top_10-2017_A10-Insufficient_Logging%26Monitoring)

For more information check this Link: [https://www.owasp.org/images/7/72/OWASP\_Top\_10-2017\_%28en%29.pdf.pdf](https://www.owasp.org/images/7/72/OWASP_Top_10-2017_%28en%29.pdf.pdf)

**Note: \*\*****  **This article will be updated with more web application attacks \*\* in the next days

## Summary

In this article, we covered the essential skills and techniques to attack modern web applications through well-known web app vulnerabilities. Later we explored the famous OWASP guidelines.

## Post updates

**\*\*\***

## References

1. Web Application Security Testing [Cheat Sheet](https://www.peerlyst.com/tags/cheat-sheet): [https://www.owasp.org/index.php/Web\_Application\_Security\_Testing\_Cheat\_Sheet#Information\_Gathering](https://www.owasp.org/index.php/Web_Application_Security_Testing_Cheat_Sheet#Information_Gathering)
2. DEFINITION Web application (Web app) [https://searchsoftwarequality.techtarget.com/definition/Web-application-Web-app](https://searchsoftwarequality.techtarget.com/definition/Web-application-Web-app)
3. Common web application architectures: [https://docs.microsoft.com/en-us/dotnet/standard/modern-web-apps-azure-architecture/common-web-application-architectures](https://docs.microsoft.com/en-us/dotnet/standard/modern-web-apps-azure-architecture/common-web-application-architectures)
4. [HTTP Header Fields - TutorialsPoint](https://www.tutorialspoint.com/http/http_header_fields.htm)
5. HTTP Headers for Dummies [https://code.tutsplus.com/tutorials/http-headers-for-dummies--net-8039](https://code.tutsplus.com/tutorials/http-headers-for-dummies--net-8039)
6. Advanced Infrastructure [penetration testing](https://www.peerlyst.com/tags/penetration-testing) Packt Publishing Chiheb Chebbi
7. [How to secure NoSQL](https://www.peerlyst.com/posts/how-to-secure-nosql-chiheb-chebbi?trk=search_page_search_result)
8. [http://projects.webappsec.org/w/page/13246955/Remote%20File%20Inclusion](http://projects.webappsec.org/w/page/13246955/Remote%20File%20Inclusion)
9. [https://www.acunetix.com/blog/articles/remote-file-inclusion-rfi/](https://www.acunetix.com/blog/articles/remote-file-inclusion-rfi/)
10. [https://medium.com/@charithra/introduction-to-csrf-a329badfca49](https://medium.com/@charithra/introduction-to-csrf-a329badfca49)
