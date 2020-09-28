# **How to Perform Open Source Intelligence (OSINT) with SpiderFoot**

In this module we are going to explore a powerful OSINT tool called &quot;SpiderFoot&quot;. OSINT or &quot;Open source intelligence&quot; is collecting publicly available information about a specific target.

![](https://securitytrails.com/user/pages/blog/099.steve-micallef-spiderfoot/spiderfoothx-visualize.png)

[Image source](https://securitytrails.com/user/pages/blog/099.steve-micallef-spiderfoot/spiderfoothx-visualize.png)

Before discovering the tool, let&#39;s explore some important terminologies

## Intelligence

The fuel of intelligence gathering is to get publicly available information from different sources. Intelligence gathering is not important in information security and penetration testing, but it is vital for national security, and as many concepts are inspired by the military strategies, in the cyber security field intelligence gathering is also inspired by the battlefields.

![](https://img.militaryaerospace.com/files/base/ebm/mae/image/2018/12/1812maesr_mar.png?auto=format&amp;w=720)

[Image source](https://img.militaryaerospace.com/files/base/ebm/mae/image/2018/12/1812maesr_mar.png?auto=format&amp;w=720)

According to International Trade Commission estimates, current annual losses to US industries due to corporate espionage to be over $70 billion.

Intelligence gathering not only helps improve the security position of the organization, but it gives managers an eagle eye on the competition, and it results in better business decisions. Basically every intelligence gathering operation basically is done following a structured methodology.

There are many intelligence gathering categories: human intelligence, signal intelligence, open source intelligence, imagery intelligence, and geospatial intelligence.

## Human intelligence (HUMINT)

Human intelligence (HUMINT) is the process of collecting information about human targets, with or without interaction with them, using many techniques such as taking photographs and video recording. There are three models of human intelligence:

- **Directed Gathering** : This is a specific targeting operation. Usually, all the resources are meant to gather information about a unique target
- **Active Intelligence Gathering** : This process is more specific and requires less investment, and it targets a specific environment.
- **Passive Intelligence Gathering** : This is the foundation of human intelligence. The information is collected in opportunistic ways such as through walk-ins or referrals. So there is no specific target, except collecting information and trying to find something. ![](https://www.incimages.com/uploaded_files/image/970x450/getty_935620656_397725.jpg)

[Image source](https://www.incimages.com/uploaded_files/image/970x450/getty_935620656_397725.jpg)

## Signal intelligence

**Signal intelligence** ( **SIGINT** ) is the operation of gathering information by intercepting electronic signals and communications. It can be divided into two subcategories:  **communications intelligence** ( **COMINT** ) and  **electronic intelligence** ( **ELINT** ).



## Open source intelligence

**Public intelligence**  is the process of gathering all possible information about the target, using publicly available sources, and not only searching for it but also archiving it. The term is generally used by government agencies for national security operations. A penetration tester should also adopt such a state of mind and acquire the required skills to gather and classify information. In the era of huge amounts of data, the ability to extract useful information from it is a must.

**Open source intelligence ** ( **OSINT** ), as its name suggests, involves finding information about a defined target using available sources online. It can be done using many techniques:

Conducting search queries in many search engines Gaining information from social media networks Searching in _deep web _directories and the hidden wiki Using forum and discussion boards

### The OSINT process

Open source intelligence is like any methodological process is going thru a defined number of steps.In order to perform an open source intelligence you can follow the following phases:

- **Direction and planning:** in this phase you need to identify the sources,in other words where you can find information
- **Collection:**  in this phase you will collect and harvest information from the selected sources
- **Processing and collation:**  during this phase you need to process information to get useful insights.
- **Analysis and integration:**  in this phase you need to join all the information and analyse them
- **Production, dissemination and feedback:** finally when you finish the analysis you need to present the findings and report them. ![](https://www.supanet.com/upload/images/201911/osint-stages-52020.png)

[Image source](https://www.supanet.com/upload/images/201911/osint-stages-52020.png)

There are many helpful tools that you can use to perform OSINT, you can find some of them in this post:

**How to Deploy SpiderFoot**

According to its official github [repository](https://github.com/smicallef/spiderfoot):

![](https://lh6.googleusercontent.com/YQjQxaCBZL8Pve7JU3c3wEL0UhMcB1ytdAH02V-8OmTUctX8wjsZR92mNOhJqHJth7_aOCGfVg3B0TG57uic-K9K_Yeo2kE3OYWZuVLO_3-Mdf04A4baFxUO-pnZzg2JFkudyok)

_SpiderFoot __ __ is an open source intelligence (OSINT) __ __ automation __ __ tool. It integrates with just about every data source available and utilises a range of methods for __ __ data analysis__, making that data easy to navigate._

_SpiderFoot has an __ __ embedded __ __ web-server for providing a clean and intuitive __ __ web-based __ __ interface __ __ but can also be used completely via the command-line. It&#39;s written in __ __ Python __ __ 3 and GPL-licensed._

![](https://lh6.googleusercontent.com/xHiH4ykj6jwNBHCeCf2hvQ0p4f4C1afDOThExvJdShMcNLUf0IWdcOIitofYBgBXPv6SIDpjEbK-dUM7nCEgXzGgwKCDhUQaEUnUqDZ-giTgrT1OwjsJP1IE30yw37c0U8tcthI)

Spiderfoot is able to collect information about:

- IP address
- Domain/sub-domain name
- Hostname
- Network subnet (CIDR)
- ASN
- E-mail address
- Phone number
- Username
- Person&#39;s name

Now let&#39;s explore how to install Spiderfoot.

Install python3-pip:

`sudo apt-get install python3-pip`

Clone the project from its Github repository using  **git clone** :

`git clone https://github.com/smicallef/spiderfoot.git`

Enter the project folder:

`cd spiderfoot`

Install the required libraries:

`sudo pip3 install -r requirements.txt`

Finally run the project using:

`sudo python3 sf.py -l 127.0.0.1:5001`

Voila! Now you can use it freely to perform your OSINT operation.

There is another option which is using a ready-to-go Spiderfoot instance. To do it check this link: [https://www.spiderfoot.net/hx/](https://www.spiderfoot.net/hx/)

To start a new scan, click on &quot; **+ Create a new scan**&quot;

![](https://lh5.googleusercontent.com/28jDAJ4AxKoNLsjd5QbJ1vDMheyjr4KbTImVUuScBaflzO4-t2G4i14qChXvhxVVVpGqUHPaHAV-Yqukzkc7QNt6ureofuxqSDfnQSxKFZ1mG405HJk-d_6brGMrc3Q9vdyTbO8)

Enter your target and click on &quot; **Run scan now**&quot;

![](https://lh3.googleusercontent.com/Y17fHyCX9CpYnDE-8hK4KMuj1VWt-gDsb-Em8QdUvcu2hjtHwe7L4HhVEdQ-rX855l5McV_alQSwTG_oIN-Sk42fKLWC4S4o_XHvf3LEYdBnaGb4AVKIQH1pU4VZ3OwR7B7RWsM)

As you can notice from the screenshot there are some APIs that need to be added n order to use some modules.

A module is a specific entity that perform a specific task. Spiderfoot comes with a long list of modules including:

- **abuse.ch:**  Checks if a host/domain, IP or netblock is malicious according to abuse.ch.
- **Accounts:**  Looks for possible associated accounts on nearly 200 websites like Ebay, Slashdot, reddit, etc.
- **AlienVault OTX:**  Obtains information from AlienVault Open Threat Exchange (OTX)

The full list of modules can be found here: [https://github.com/smicallef/spiderfoot](https://github.com/smicallef/spiderfoot)

The tool gives you the ability to investigate data too:

![](https://www.spiderfoot.net/wp-content/uploads/2020/03/Screenshot_2020-03-01-SpiderFoot-HX1-1024x731.png)

[Image source](https://www.spiderfoot.net/wp-content/uploads/2020/03/Screenshot_2020-03-01-SpiderFoot-HX1-1024x731.png)

## Summary

In this module, we explored Open source intelligence and how to perform it using a powerful tool called &quot;SpiderFoot&quot;

