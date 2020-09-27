# Getting started using Microsoft Azure Sentinel (Cloud-Native SIEM and SOAR)

In this module, we are going to explore Microsoft Azure Sentinel (Cloud-Native SIEM and SOAR). We are going to learn how to deploy the SIEM from scratch and we are going to see how to start detecting threats with it

![](https://danielchronlundcloudtechblog.files.wordpress.com/2019/07/sentineldashboard.jpg?w=1100)

[Source]()

Before learning how to use Azure Sentinel, we need to define it first. According to one of  their official [blog posts](https://azure.microsoft.com/en-in/blog/introducing-microsoft-azure-sentinel-intelligent-security-analytics-for-your-entire-enterprise/):

> Azure Sentinel provides intelligent security analytics at cloud scale for your entire enterprise. Azure Sentinel makes it easy to collect security data across your entire hybrid organization from devices, to users, to apps, to servers on any cloud.  It uses the power of artificial intelligence to ensure you are identifying real threats quickly and unleashes you from the burden of traditional SIEMs by eliminating the need to spend time on setting up, maintaining, and scaling infrastructure.

Most of the first steps are already discussed in details in the previous resource. Thus I am going to go through the steps rapidly:

Go to Azure search bar and look for Azure Sentinel (preview) and add a new workplace

![](https://lh4.googleusercontent.com/HZjIAkhgRpz-XWsnWd5utgDVB5fd0SxZ8oHNFUmeWFsManYfpjfqS3FG06Sv-Ph9HrCM7sz7Q274qT6XzUBuPqbkT9qy1D8h_8-hvXz8YeNs8Z_wi-oTkD0HNsrbnPVaQ1ui4gw)

Create a new Workspace and press &quot;OK&quot;

![](https://lh5.googleusercontent.com/_Z-mkYo33YwiIqMHpqqVSg2P2XneKL5AWXs1tBU0x6zA4uIpnAu2QYvVBKEodaTFlw11xMkyS7Q_R1f04tg_1vYA9zGB0Orxc4IAVniGz7UV2u8DO9t_kWhbb4NeYgADmReVVFc)

Add a new Azure Sentinel

![](https://lh5.googleusercontent.com/Lq6JhzZje6YVRkxRMIQf-Gizi9Qdo-pkj_g-gusOY8-QwOxOl4ziOjl43JP06I_aLYSHghO98weUrdXmYIj9iiTd9rpz_7FL-wF9yduqVUIBsAlr_oUsrpD896FQyWt-EcPVyuw)

Voila!

![](https://lh4.googleusercontent.com/Ei7mbVX4320hFy3kJc08XfeI7DVY-yumFstdTtxFNK8YFSHhXR_ZgWY3UEM2iuQDZtQDSx-aORpYlB6NkiaPhAH7q2s-kL3TF1a073rrvkxal79pTRFpzKiInOImTYsEZVTLldU)

Now you need to select a connector to receive logs:

![](https://lh5.googleusercontent.com/NbB1ti7CfCNUpdKIZNwfuGYBjsg9J8r9sD5q6SA6DB0YibE7ySpI5HYoXRR5TNy5fs4RFuJ10cvB5unCtxI4ftG4n2oSDQzgukAGpDq0I21oAKnWx2v5l4LMAYzIC5U7-NPobTs)

For example, you can select Azure Activities:

![](https://lh4.googleusercontent.com/MkXDDPbWgWVdacW5ezjiMavxtvf4WP6iuredJ7AiK7_8ilNCCzr0iGVSQitIdqG1M9ybtFHFoIxbzrBJXQgdYfsPIKwxXshwkn0QXiql31A9W1HAyBe_UNGiXFb3-aSufKd06v4)

Click &quot;Next Steps&quot;

![](https://lh3.googleusercontent.com/1-738_rNgDFbeEvyV5GLVw5ZzI8foa8Iwol_5ehLAbUtgoFQKLDDRTt2OEKy-UiS1tYdozhl9JwkceqILB3sNDH29IG-2et54VOMj0sv1BA86eCYwHzGHMJIje3AJvEKJZKgMBg)

![](https://lh3.googleusercontent.com/wA2LvAyzyuTWzyTmvgZUx7tEzPS_g7BPzkkGqYWfZ7jDqwQZtXTyzk9nooxPuN_FYuGqzcjIhkKCfKUyicI-v55Bc9nFoB7x7R4h9dj8VPOnhjB8onHpYb9CWBAp3h_ZLlMhyCw)

Create a Dashboard. The following graph illustrates some of the Dashboard components:

![](https://lh3.googleusercontent.com/PSPBsMFgHSZw-DsblKYXaO2OJG1ngq0jEq-EiXpLr1xsbAQhlg3mLLreZaxNXCYbebglOoTYNIrDN7iyiY9_m46qrYqCieXascKd7ZQvEPI1PcUQKBFSY05_3b1Z9IeiZKxF-z0)

![](https://lh6.googleusercontent.com/WEkwrrgV-TQt5KZl_Afl4pmjxVPc4UxMvqrgq4paPkwlr4_uZfgeWUBHGY9hfMt9ow9klGRee7znM6fp_uZw0cWvKJob0C8Sy_LXSxjuAFkcnWIRhvpvkJyeQCIUXPLBjxB9y78)

![](https://lh5.googleusercontent.com/O4ljwxA08Ony2yKqs_XMQMZAIJXAIXgL_dRuWu251CmDTz0RY4qo7feDZYW26w9mXMwdreMB5kmtEb2jZe58b_-9lmRagZF77QntiiPa1DlmRIKjs36A9MIEM0E6p9JeKIOuFUM)

If you want to receive logs from an Azure VM you can select the  **Syslog Connector ** and pick the VM that you want to use:

Deploy the Linux agent for example in &quot;Zeek&quot; VM

![](https://lh4.googleusercontent.com/rU1rM1p4_xYoGy4FJwApidblS7yELGBFjwI4LjUQ1ks8M4V9r1GusfL6wh7byGqEWMbpOz4RaDw7n12uVpW-XFxY_IsgeODGvExVhfBDogP2x0b_k9UhvHoa3w9TkUdlwl089rg)

Go to &quot;Advanced Settings&quot; - \&gt; Data - \&gt; Syslog - \&gt; select Apply below configuration to my machines

![](https://lh4.googleusercontent.com/jjlPdC_NTiFtpSwKBRhm9NDdU1aHOSLIudOhCsLGLmesCqIF-kzLzeuNdvsRrNMGhbWPXtDOb6jpkvoRSJ85L8eipuSZJkE4i-2NptvnvlMZH3gqTv_2hrLgJ4NEYVtK6ThC6YI)

And now you are connected the Linux Machine

![](https://lh3.googleusercontent.com/Bkd68CLKm6QsjeBGegVl40fQOhbF8DYzVpHeJrgsVltplUuQ80s592lwJ1O37gJPfsLTWXulqWoZhAgwB3tWoXWYCuyVU7WuTElq2Kpk0XXaUru9CyeRYCY7KPnBOsvjHKP3QZ4)

If you want to receive logs from a windows machine: Go to  &quot;Advanced Settings&quot; - \&gt; Connected Sources and select &quot;Windows Servers&quot;. Then download the Windows agent installation binary

![](https://lh5.googleusercontent.com/4T1hPjKBneTQDBJNHc-_xBPsaBXm8cU6XN0hETYV2NUz72OfCLCL2SX1S5z9-MNceym06UjUlkdkAUXNkID1mLk85xUNmZLVpacptjqqxXjfCXJkBy1R_jtKkrjp1RuxQVzSmRU)

Open your Windows machine (in my case  **Windows 7 x32** ) and install the agent. Click  **Next**

![](https://lh6.googleusercontent.com/2kJg7BqJhJfzewkGGrIu_MY5ObfIa-CYRT5NoNqFHSeRBDujLtrAw_Pvx8laRykN8l8jghm_gM4WIyDFI2ORdSL_fSeWWB55she4RTVpPmSI4D6XzsO04x1kbtbR3qbOF-sn5rU)

Add your  **ID**  and  **Key**  (You will find them in Windows servers dashboard )

![](https://lh4.googleusercontent.com/lR3uPn7C2pYCV-hX-nVERC9d55hzLRYgg8iQ4svVX9oat5M5BuIzwzkBqwiVOCSHU3FYv9bUm8KQX2Zrmz7WQuX1bsAMUV71hEMAwh9ggbMYFK2JbUM7Z-Txyhww30c2UG5Bj1c)

Click  **Next**  and you are done

![](https://lh5.googleusercontent.com/LqB_wMhQ7QurGDrhUMovNAzomuRm81OCAn8S-75TK-rpEkse73NDKCQ9VLHBOcOznoMN2CdNISZLbqRQyIIn_6PvU1zKE1_p5fXBOp0mFwUvk3RTxVflE9_-ddJK5-0U3aJ1eW4)

Now it is hunting time! Go to your Sentinel page and select  **Hunting**  and you will be able to type your own hunting queries using KQL Azure query language.

![](https://lh3.googleusercontent.com/nOY9LQV0mEeuI42mw7mPCzNujQZmTYyw-NANK-UK_8t5rpr2zGg6MYqWOfxzHhk132_9v7Bp43V0sViEEMg94yA6C45n9zTrNQmLl7Poh47s2J2n2rxvKio7kJEkchSlVTEDKOU)

You can also use and create your own Notebooks

![](https://lh5.googleusercontent.com/c70rw1toxCGdI3D7037uuU1hqXg_4jJXlLGF-_AVFTz6k_UZTrqcIovdBLy6Ru9lJznPWgKVReKU--P0J9j5XfSiK0VL9H5UU09TygywddUhjuKY38YrqRC8PsKAdOLN5ZiTNzw)

You can use some pre-made hunting notebooks delivered by Azure.  **Click Import**

![](https://lh5.googleusercontent.com/J1FJNgQocQZLPxhCDuo3Y3jtWYnmkcW3V2BQtuRCjAZkjH2g7c2Zm-DZLzFulaAT_KUm02db1yLRMpoe4cVwq7XRhkbnwLNwEUZB1-irnyObD860fKCoR3UtGaEydlrcVDxUk9E)

and you will upload them directly from the official Sentinel GitHub account: ![](https://lh5.googleusercontent.com/8lJV_3XARblFmiNa_ypArC3XlUvKcLBfmNgAnWVcQIl9EUoXF2NLyomojjv0cfZQ21cuR7Ay3GJ0v8vre7QbQfDTz4pOmVEIX01uWhVTl1_ThxgjRGJW32paTGcn2ozIVyJcmdk)

The Sentinel dashboards are highly customizable. In other words, you add any visualisation you want. In this example i added a CPU visualization

![](https://lh6.googleusercontent.com/O11OCUotqZSngm4-F177SWtuZLV8ttaIryARzcnrjWlcPdU18Zq2K-LP2H7CHI8mG51otWviucsRN5D30PySrh5SDA4Yy9FtNnh1ukFJRXEQ06qYMDPQVswrhM-o6Cf5kTEcGPw)

You can even add your alert/detection rules. If you want to do so click  **&quot;New alert rule&quot;**

![](https://lh6.googleusercontent.com/yxFwWGJb1C3bHjSnwZXSXdj5qGMDpJYsIJi9w2sH2zCWKk3facbYtBSFaExvHW-L26wNO7yjwIpdNN3xZhnD5r8x0VDgLtIkFnfZnmv4vjGgxLywoGjhj_49DuBRr5C6UxwmsIc)

![](https://lh6.googleusercontent.com/dvm_gRv2V12FiI6ayVL1OAqPSj75mLMlRxbMPGipi39PF-dKQLR4w-OY7VwfGMUEo94O4sLHGKgiLzD4z0hlbhCofp-MmKklWxJLAz-on5vDxlX-wmCFGK_UAa2_OovlfNVu0Mc)

I tried an arbitrary condition for educational purposes  **CPU \&gt; 1.4% **
 ![](https://lh5.googleusercontent.com/OPAbLIN1nPwcZ6bDJeC4w3nBlTO6tQUQDU10o8np3G6fUdsiQkhhryfDLFafDD8LfC4rUNGj0SMh9fsEe4swGbwLOK0_taw5pwGpQQ9eW2wjEfwaZsOXeiAfzu_jfhpL4mCYcBw)

You can also select your action when the condition is performed. In my case, i tried the email notification option

![](https://lh4.googleusercontent.com/fYQq0kwpq1M9BKzG8n2KUOyaqlxE5JueV9XQYm3SfH1Pb4z9XOM6AO0tYp44Oq3ok7zKtnV7W6SRe8GTIyzN-N-2qCTSJP_vKiRdJ5oG0qAHGyYvup3oe_1ybzviSKF7GI0nVUk)

You will receive a confirmation email to check that everything is ok:

![](https://lh3.googleusercontent.com/nYChvWtRHfZ4QlMudy8owl4vWAKGn4kMeaxFjnM7b8p3KueY_8kvTp6pQafdyW41kImI3M_zGpqxIih6gSRafkGePdN9r7ZSbHOCsdBmsZWJii0LdP0dyVX9pmHV_5Xxt5ExkJg)

When the rule is achieved you will receive an email notification

![](https://lh5.googleusercontent.com/OCtuAb7lfiGBorXIThd82_moG9zknWxo7SIkyfZWHm1_Zzx9jAxt52QjoIm1wHV1CDga17XKb6MFaCybIxrF0hee9GgTbnQyklnvKL_9gxUw5mC4zxQaEvQh6Vyp7-xi-7lihAI)

You can also write your own advanced detection queries with KQL. Go to &quot; **Hunting**&quot; and Click &quot; **New Query**&quot; and create your customized query and also you can identify its connection with MITRE ATT&amp;CK framework.

![](RackMultipart20200926-4-o5tfaf_html_4e021d847b722091.png)

By now you are ready to start your Hunting mission.

I hope you found it helpful. If you need me to correct something please don&#39;t hesitate to comment on this post.

