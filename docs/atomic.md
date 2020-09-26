Hi Peerlysters,

 Modern organizations face cyber threats on a daily basis. Black hat hackers do not show any indication that they are going to stop. New hacking techniques appear regularly. According to multiple information security reports, the number of APT attacks is increasing in a notable way, targeting national defenses, manufacturing, and the financial industry. Thus, classic protection techniques are, in many cases, useless. Deploying suitable platforms and solutions can help organizations and companies defend against cyber attacks, especially APTs. Some of these platforms are attack simulation tools. In this article we are going to learn how to deploy a red teaming simulation platform called _ **Atomic Red Team** _.

![](RackMultipart20200926-4-kwa6fy_html_dc47ece56df401ef.png)

[Image source](https://www.redcanary.com/wp-content/uploads/image2-25.png)

**But first what is  Red teaming? **

Techtarget defines red teaming as follows:

&quot;_ **Red teaming** __ is the practice of rigorously challenging plans, __ policies __, __ systems __ and assumptions by adopting an __ adversarial __ approach. A __ **red team** __ may be a contracted external party or an internal group that uses strategies to encourage an outsider perspective.&quot; _

![](RackMultipart20200926-4-kwa6fy_html_853c2c05db73c96b.jpg)

[Image source](https://i1.wp.com/www.omanobserver.om/wp-content/uploads/2019/09/cyber-attack.jpg?resize=800%2C445&amp;ssl=1)

Red Teamers usually perform the following steps:

- Recon
- Initial compromise
- Establish persistence
- Escalate privileges
- Internal Recon
- Lateral movement
- Data analysis
- Exfiltrate and complete mission

![](RackMultipart20200926-4-kwa6fy_html_76b9e4720ed85fde.jpg)[Image source](https://camo.githubusercontent.com/7ed924f85b775db73958b443a8798b401c40cdd2/68747470733a2f2f75706c6f6164732d73736c2e776562666c6f772e636f6d2f3538383636636165616263383364356537633537346337312f3538626534333132646331336239646537343638363132615f5265642d5465616d2d41747461636b2d4c6966656379636c652e6a7067)

To learn more about red teaming i highly recommend you to check InfosecTDK‍ &#39;s article:

**Atomic Red Team**

According to its official Github [repository](https://github.com/redcanaryco/atomic-red-team)

  ![](RackMultipart20200926-4-kwa6fy_html_749da0e6c24c1e60.png)

_Atomic Red Team allows every security team to test their controls by executing simple &quot;atomic tests&quot; that exercise the same techniques used by adversaries (all mapped to _[_Mitre&#39;s ATT&amp;CK_](https://attack.mitre.org/wiki/Main_Page)_). Atomic Red Team is a library of simple tests that every security team can execute to test their controls. Tests are focused, have few dependencies, and are defined in a structured format that can be used by automation frameworks._

MITRE ATT&amp;CK is a framework developed by the Mitre Corporation. The comprehensive document classifies adversary attacks, in other words, their techniques and tactics after observing millions of real-world attacks against many different organizations. This is why ATT&amp;CK refers to &quot;Adversarial Tactics, Techniques &amp; Common Knowledge&quot;. A tactic is the highest level of attack behaviour. Techniques are used to execute an attack successfully

![](RackMultipart20200926-4-kwa6fy_html_d932f4fa66137917.png)

MITRE framework present the tactics as the following:

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

Let&#39;s explore how to install and use Atomic Red Team:

First you need to download the project from here: [https://github.com/redcanaryco/atomic-red-team](https://github.com/redcanaryco/atomic-red-team)

![](RackMultipart20200926-4-kwa6fy_html_6e43af7f6899f8d4.png)

Disable Windows defender

![](RackMultipart20200926-4-kwa6fy_html_7da32eb7df694f92.png)

Extract the zip file:

![](RackMultipart20200926-4-kwa6fy_html_5c4a3604b052e212.png)

The techniques can be found in the &quot;atomics&quot; folder:

![](RackMultipart20200926-4-kwa6fy_html_28c96def7b97ba0.png)

Now Open powershell and type:

powershell -ExecutionPolicy bypass

![](RackMultipart20200926-4-kwa6fy_html_2a3bfe985f71d21f.png)

Install a required module:

Install-Module -Name powershell-yaml

![](RackMultipart20200926-4-kwa6fy_html_515f37a1e11e6565.png)

Now go and download  **Invoke-atomicreadteam**  from: [https://github.com/redcanaryco/invoke-atomicredteam](https://github.com/redcanaryco/invoke-atomicredteam)

_Invoke-AtomicRedTeam is a PowerShell module to execute  __tests__  as defined in the _[_atomics folder_](https://github.com/redcanaryco/atomic-red-team/tree/master/atomics)_ of Red Canary&#39;s Atomic Red  __Team__  project. The &quot;atomics folder&quot; contains a folder for each  __Technique__  defined by the _[_MITRE ATT&amp;CK™ Framework_](https://attack.mitre.org/matrices/enterprise/)_. Inside of each of these &quot;T#&quot; folders you&#39;ll find a  __**yaml**__  file that defines the attack  __procedures__  for each atomic test as well as an easier to read markdown ( __**md**__ )  __version__  of the same data._

![](RackMultipart20200926-4-kwa6fy_html_8ad38d387dddccfe.png)

Enter the project folder and then type:

Import-Module ./Invoke-AtomicRedTeam.psm1

![](RackMultipart20200926-4-kwa6fy_html_f2c0c8a546f55346.png)

Now you can run any test you want by simply run the following commands:

$TXXXX = Get-AtomicTechnique -Path \path\to\atomics\TXXXX\TXXXX.yaml

Invoke-AtomicTest $TXXXX

The techniques can be found in the first downloaded project

![](RackMultipart20200926-4-kwa6fy_html_1035af5acc8c8534.png)

I hope you will find it helpful

**References: ** [
](https://bestestredteam.com/2019/07/30/atomic-red-team/)

- [https://bestestredteam.com/2019/07/30/atomic-red-team/](https://bestestredteam.com/2019/07/30/atomic-red-team/)
- [https://bleepsec.com/2018/11/26/using-attack-atomic-red-team-part1.html](https://bleepsec.com/2018/11/26/using-attack-atomic-red-team-part1.html)

**Further resources: **
