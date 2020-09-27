# **Getting started with IDA Pro**

Hi Peerlysters,

![](https://lh6.googleusercontent.com/Ha65AuSfzRhri77CzdK0fTAje1o4wGbV2Cq8cN3pKRg8pxMaQnLxlWDeMfokvFyo8dizEPdpbADB4detcmMlut3o5-pZaegjChaozjoJfu4-ny4yI4I2M_viRCZEt8FnIsJmiC4)

Reverse engineering is a very important task in information security. It is highly performed in digital forensics, binary exploitation, vulnerability analysis, malware analysis and much more. In this article, we are going to explore an amazing tool called &quot;IDA Pro&quot;.


**Installation **

According to its official website,

&#39;_IDA is a  __Windows,__   __Linux__  or Mac  __OS X__  hosted multi-processor  __disassembler__  and  __debugger__  that offers so many features it is hard to describe them all&#39; _

There are two versions of IDA:

- Commercial version &quot; **IDA Pro**&quot;
- A free version of it called &quot; **IDA Free**&quot;

![](https://lh5.googleusercontent.com/NwGbmt8ZrJluRvHuGOR3B5_lNC3_obGVdsHwXLDDc-4l__ku-i-znwSEQPb-InziAclNdloSZYYQiZbwdcXxPJpJcUdofPfjXdKvxD_eIBIBy-drzOgwnaxb3QsuvC7AdqZf-HA)

[source](https://www.hex-rays.com/products/ida/pix/idalarge.gif)

To install IDA Pro on Windows you just simply need to go to: [https://www.hex-rays.com/products/ida/support/download.shtml](https://www.hex-rays.com/products/ida/support/download.shtml)

![](https://lh5.googleusercontent.com/2un-_OQEiqOm30KYve2HtGPgioGkatr2hrd6Px-pS-vPCafH_QVvm8QvAdehLnEfG1PkBzqHA3-0k4IPinNWS5sfhWWYkVo_xeRF95KpPPZ9bMNv5WCPHDMw_nSWSncMJTJi7JA)

After installing it you can start it from its desktop shortcut

![](https://lh6.googleusercontent.com/621F2owSKOkYJQaSpO9zULHLNL-qmSPNUlDgIDXqwAfuvr0k4c5FR2vKGdgBBxXeUB_bLWHc0EpuqjjgAPboNdI4f8IGgjtDMOXnFwS1JYw-K4oDIZraodJc3UjV9EtoOuknLpk)

Once you start it, you will have the choice to work on  a new project and load an old disassembly

![](https://lh3.googleusercontent.com/ZwUjIKv9CixSvtHVjMNBjufVEqNmuvWe2qxk202DFtJaIVsPyw8FDqCOjyOgv0lZw0gs-SoD_G_LRYHbhp4_Lm92UZQmiRxs_03gMR6MYBPH2DDfztvefzMADApfj6AbqxRZhjw)

As a demonstration, we are going to disassemble a simple malicious PE file from Paloalto Networks. You can download it from here: [https://docs.paloaltonetworks.com/wildfire/7-1/wildfire-admin/submit-files-for-wildfire-analysis/test-a-sample-malware-file](https://docs.paloaltonetworks.com/wildfire/7-1/wildfire-admin/submit-files-for-wildfire-analysis/test-a-sample-malware-file)

![](https://lh3.googleusercontent.com/9ml1MkUY3Ayn6S02oPUj01gT6K5rpGvLIosVKa_1WKFEvKr8MwFzeZIkERxHA2LEmnIRq4rRTssoqROqsJ1uImmnk-VnSXBYGFLemCK1BMU-13K0xc7LD5E5ALBL2xU95sW2kHs)

Don&#39;t forget to test the file on a sandbox or a VM

**Portable Executable ** ( **PE** ) files are file formats for executables, DDLs, and object codes used in 32-bit and 64-bit versions of Windows. They contain many useful pieces of information for malware analysts, including imports, exports, time-date stamps, subsystems, sections, and resources. The following is the basic structure of a PE file:

![](https://lh4.googleusercontent.com/sKRveUnF2Xy2XveSGbI4Qw7bMozwKrA4pq-BjQSYv3OX48kRW3MSwCAGe_a6Vz_iKutWtHZe36RlaOiM5bURciVausSkTr3M5aw-9V24nCCBBmpQmcN8KhHlbt-_g4ZdxVnzK8g)

Source: [pe\_format.png](https://i2.wp.com/dandylife.net/blog/wp-content/uploads/2015/02/pe_format.png)

Some of the components of a PE file are as follows:

**DOS Header** : This starts with the first 64 bytes of every PE file, so DOS can validate the executable and can run it in the DOS stub mode.

**PE Header** : This contains information, including the location and size of the code.

**PE Sections**  They contain the main contents of the file.

Load the PE file:

![](https://lh4.googleusercontent.com/F3sosLege87TWKRYn5ZuSDVVk8ivFlPv6_ssk0wFDmj4XS17sVl-q3xyAeoi7cs0AXsoIUoAsuFF_2r-8FfTzepbLUvvdQaLdxXlj46wkQJiVQO8LedcgK9ItOPr0-1LdILNVbk)

As you can see from the previous screenshot, IDA Pro is able to detect the file type automatically.

Press &quot;OK&quot; and will be guided to the main interface:

![](https://lh3.googleusercontent.com/m1H3ysapEnNjSHaoilD2ZE4eIqG_BG66Ydiri-8T87ui0pB8rRlQdLAI0uzhTzJRVPPftGm-cr9Sb2wbUBea1bosu4lWiNHtP3qiDtxScD6jE-rFM6HbNBZZhalCJW7zOcBLN5I)

If you load a file, IDA will create a database &quot;_idb_&quot;. The database contains:

- **Name.id0**
- **name.id1**
- **name.nam**
- **Name.til**

The main interface contains  many views and windows:

This bar called &quot;the navigation band&quot; illustrates the memory space used by the binary

![](https://lh5.googleusercontent.com/6lXYRcWzNrH76iRDUGUtkSw_SlYpLJ0pfVwDgRsKy9vf4Qc9AB3eJazGtHy3rOxKeBUi7jqs5BOFe9a73exKa2-fXKsK1hA1fWYl9thdlwAe_zQz9vsTnKUq0OKXQmsWFAoX7sQ)

There is also a graph view to display functions as graphs and sub-graphs

![](https://lh3.googleusercontent.com/94tOHfNkAkq33O0ZDjuc7wII72Qe649_vkO3sBn6Sv1cMAO8qdy8TlQiKS0G4H5JxByY5mGcAzor4lGGC5BrMRNhrDBGCayETdbacVFlILNs7h0n5Vb3aPdikfD-JythCGkqtF0)

**Functions Window: **

It lists all the recognizable functions by IDA pro

![](https://lh4.googleusercontent.com/w0YmoChoqMl6mHGB0qRTjmaZcWcXS6edr0BokhSCMrlpQe8DPgGG-r-vbGw3vUBjhTldiyalW3j0seHaugk55rfpWIWeJDK9Zwh1edI6mZj8J5kS56znZvmhPIQCNRvlnB8DEkQ)

**Imports**

It shows the imported libraries by the loaded binary

![](https://lh4.googleusercontent.com/szMB66htI2RFvhXUkcAld_91sV6-_Xlj7D3WdojWV40AEMFgJ1sFFXGDA3olNaDt1ReA-bJh9gqZOI-iiDAXb72e5g-_xD-hEdW7AxkjqaxQZtAXxM1HvaxK0hVcKgcTjhcv1Rw)

The following is the text view where data is represented as disassembly

![](https://lh5.googleusercontent.com/YO6bFvpSQDUXeieXO-AHR-SoParVp_YeCc-hO_XU7co4m-7Izjp9fk4z7yYm2xmvm-e23HyX0Anz-3RRDG1E7cl1dLTTvjEph13xesq3Q9tlDOm_3UmXZBcr74fjm6TXg_oCmcE)

You can find a lot of other available views: ** view -\&gt; Open Subviews **

![](https://lh5.googleusercontent.com/hl-gLOxAly7IY4uVbCuG6-6sgwRZufcHHwEUiW8Y_jVE2ZIvu0GSFrwjxrYoslAvmQflXYa-au6scjcRf0tM5NweqLdsb0kO_z92DPPvhe62ov9HwRa3vjMveaI93MDiRF1g0nY)

To facilitate the navigation you can simply use the IDA shortcuts including:

Go to a new window: Alt+Enter
 Text: Alt+T
 Names: Shift+F4
 Functions: Shift+F3

You can find the full list here:  [Datarescue Interactive Disassembler (IDA) Pro Quick Reference Sheet](https://www.hex-rays.com/products/ida/support/freefiles/IDA_Pro_Shortcuts.pdf)

Based on its great capabilities IDA Pro is very helpful when it comes to Malware Analysis since it gives you the ability to extract many pieces of information including Strings (F21), imports, exports, graph flows and so on:

![](https://lh5.googleusercontent.com/Qzy0yU61HCqtoYUDUfRicF3k8N9zkulsBW7gywl8HsEvV7tWZ6AmrySwgIBPjTMab79DIMnjutq9dSKRgiyU8MzWLjfWs6dNN3UYHSG_RvS_qRidtXZRWFdR0VT5JUCuwodWVzI)

If you want to explore another great tool, I highly recommend you to take a look at my article:&quot; **How to Perform Static Malware Analysis with Radare2**&quot;

In this article, we did a high-level overview of IDA PRO
