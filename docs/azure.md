# Getting started using Microsoft Azure Sentinel (Cloud-Native SIEM and SOAR)

In this module, we are going to explore Microsoft Azure Sentinel (Cloud-Native SIEM and SOAR). We are going to learn how to deploy the SIEM from scratch and we are going to see how to start detecting threats with it

![](https://danielchronlundcloudtechblog.files.wordpress.com/2019/07/sentineldashboard.jpg?w=1100)

[Source]()

Before learning how to use Azure Sentinel, we need to define it first. According to one of  their official [blog posts](https://azure.microsoft.com/en-in/blog/introducing-microsoft-azure-sentinel-intelligent-security-analytics-for-your-entire-enterprise/):

> Azure Sentinel provides intelligent security analytics at cloud scale for your entire enterprise. Azure Sentinel makes it easy to collect security data across your entire hybrid organization from devices, to users, to apps, to servers on any cloud.  It uses the power of artificial intelligence to ensure you are identifying real threats quickly and unleashes you from the burden of traditional SIEMs by eliminating the need to spend time on setting up, maintaining, and scaling infrastructure.

Most of the first steps are already discussed in details in the previous resource. Thus I am going to go through the steps rapidly:

Go to Azure search bar and look for Azure Sentinel (preview) and add a new workplace

![](RackMultipart20200926-4-o5tfaf_html_89871198da4a827b.png)

Create a new Workspace and press &quot;OK&quot;

![](RackMultipart20200926-4-o5tfaf_html_65283fa081fc82b2.png)

Add a new Azure Sentinel

![](RackMultipart20200926-4-o5tfaf_html_2e676d719bb7fa62.png)

Voila!

![](RackMultipart20200926-4-o5tfaf_html_4e1cefab912c4f45.png)

Now you need to select a connector to receive logs:

![](RackMultipart20200926-4-o5tfaf_html_16fba36c6a31ec26.png)

For example, you can select Azure Activities:

![](RackMultipart20200926-4-o5tfaf_html_b12bbd0a247f35.png)

Click &quot;Next Steps&quot;

![](RackMultipart20200926-4-o5tfaf_html_8c6b645bdf3b256b.png)

![](RackMultipart20200926-4-o5tfaf_html_252de9d5898676fa.png)

Create a Dashboard. The following graph illustrates some of the Dashboard components:

![](RackMultipart20200926-4-o5tfaf_html_ed01e9fb0f7e5ec4.png)

![](RackMultipart20200926-4-o5tfaf_html_7b36d762e7ab683b.png)

![](RackMultipart20200926-4-o5tfaf_html_e99a1bc24db190e9.png)

If you want to receive logs from an Azure VM you can select the  **Syslog Connector ** and pick the VM that you want to use:

Deploy the Linux agent for example in &quot;Zeek&quot; VM

![](RackMultipart20200926-4-o5tfaf_html_d3d0b1cd9f6232a1.png)

Go to &quot;Advanced Settings&quot; - \&gt; Data - \&gt; Syslog - \&gt; select Apply below configuration to my machines

![](RackMultipart20200926-4-o5tfaf_html_c9bb62800d330ceb.png)

And now you are connected the Linux Machine

![](RackMultipart20200926-4-o5tfaf_html_38b87568a9ad9389.png)

If you want to receive logs from a windows machine: Go to  &quot;Advanced Settings&quot; - \&gt; Connected Sources and select &quot;Windows Servers&quot;. Then download the Windows agent installation binary

![](RackMultipart20200926-4-o5tfaf_html_ea66f231146c070a.png)

Open your Windows machine (in my case  **Windows 7 x32** ) and install the agent. Click  **Next**

![](RackMultipart20200926-4-o5tfaf_html_a32e0df6a71d34d.png)

Add your  **ID**  and  **Key**  (You will find them in Windows servers dashboard )

![](RackMultipart20200926-4-o5tfaf_html_3829aad2ca7a7ec7.png)

Click  **Next**  and you are done

![](RackMultipart20200926-4-o5tfaf_html_345316fbd96d5f30.png)

Now it is hunting time! Go to your Sentinel page and select  **Hunting**  and you will be able to type your own hunting queries using KQL Azure query language.

![](RackMultipart20200926-4-o5tfaf_html_6d653ff3fa879791.png)

You can also use and create your own Notebooks

![](RackMultipart20200926-4-o5tfaf_html_29b37ff9474046ed.png)

You can use some pre-made hunting notebooks delivered by Azure.  **Click Import**

![](RackMultipart20200926-4-o5tfaf_html_8effc420a2ba4b5b.png)

and you will upload them directly from the official Sentinel GitHub account: ![](RackMultipart20200926-4-o5tfaf_html_23d5f77ae247392f.png)

The Sentinel dashboards are highly customizable. In other words, you add any visualisation you want. In this example i added a CPU visualization

![](RackMultipart20200926-4-o5tfaf_html_feb44d4168cdb99a.png)

You can even add your alert/detection rules. If you want to do so click  **&quot;New alert rule&quot;**

![](RackMultipart20200926-4-o5tfaf_html_4396de5a0b5732f4.png)

![](RackMultipart20200926-4-o5tfaf_html_616ca10170ac8c92.png)

I tried an arbitrary condition for educational purposes  **CPU \&gt; 1.4% **
 ![](RackMultipart20200926-4-o5tfaf_html_212b885c0f2680c5.png)

You can also select your action when the condition is performed. In my case, i tried the email notification option

![](RackMultipart20200926-4-o5tfaf_html_242620b3fce04b4f.png)

You will receive a confirmation email to check that everything is ok:

![](RackMultipart20200926-4-o5tfaf_html_fbf51a6fbde16e3e.png)

When the rule is achieved you will receive an email notification

![](RackMultipart20200926-4-o5tfaf_html_a06b47ddf4f304bb.png)

You can also write your own advanced detection queries with KQL. Go to &quot; **Hunting**&quot; and Click &quot; **New Query**&quot; and create your customized query and also you can identify its connection with MITRE ATT&amp;CK framework.

![](RackMultipart20200926-4-o5tfaf_html_4e021d847b722091.png)

By now you are ready to start your Hunting mission.

I hope you found it helpful. If you need me to correct something please don&#39;t hesitate to comment on this post.

