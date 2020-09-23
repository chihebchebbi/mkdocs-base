# **Getting started with IDA Pro**

Hi Peerlysters,

![](RackMultipart20200923-4-nfhana_html_775f14123074bbd7.jpg)

Reverse engineering is a very important task in information security. It is highly performed in digital forensics, binary exploitation, vulnerability analysis, malware analysis and much more. In this article, we are going to explore an amazing tool called &quot;IDA Pro&quot;.


**Installation **

According to its official website,

&#39;_IDA is a  __Windows,__   __Linux__  or Mac  __OS X__  hosted multi-processor  __disassembler__  and  __debugger__  that offers so many features it is hard to describe them all&#39; _

There are two versions of IDA:

- Commercial version &quot; **IDA Pro**&quot;
- A free version of it called &quot; **IDA Free**&quot;

![](RackMultipart20200923-4-nfhana_html_b2b22886b113b98c.png)

[source](https://www.hex-rays.com/products/ida/pix/idalarge.gif)

To install IDA Pro on Windows you just simply need to go to: [https://www.hex-rays.com/products/ida/support/download.shtml](https://www.hex-rays.com/products/ida/support/download.shtml)

![](RackMultipart20200923-4-nfhana_html_969213f67e8a0550.png)

After installing it you can start it from its desktop shortcut

![](RackMultipart20200923-4-nfhana_html_f81040c2a78bcc69.png)

Once you start it, you will have the choice to work on  a new project and load an old disassembly

![](RackMultipart20200923-4-nfhana_html_1d7a7fb18560e5b5.png)

As a demonstration, we are going to disassemble a simple malicious PE file from Paloalto Networks. You can download it from here: [https://docs.paloaltonetworks.com/wildfire/7-1/wildfire-admin/submit-files-for-wildfire-analysis/test-a-sample-malware-file](https://docs.paloaltonetworks.com/wildfire/7-1/wildfire-admin/submit-files-for-wildfire-analysis/test-a-sample-malware-file)

![](RackMultipart20200923-4-nfhana_html_d33c62efbec01393.png)

Don&#39;t forget to test the file on a sandbox or a VM

**Portable Executable ** ( **PE** ) files are file formats for executables, DDLs, and object codes used in 32-bit and 64-bit versions of Windows. They contain many useful pieces of information for malware analysts, including imports, exports, time-date stamps, subsystems, sections, and resources. The following is the basic structure of a PE file:

![](RackMultipart20200923-4-nfhana_html_356b22d31ec24cf1.png)

Source: [pe\_format.png](https://i2.wp.com/dandylife.net/blog/wp-content/uploads/2015/02/pe_format.png)

Some of the components of a PE file are as follows:

**DOS Header** : This starts with the first 64 bytes of every PE file, so DOS can validate the executable and can run it in the DOS stub mode.

**PE Header** : This contains information, including the location and size of the code.

**PE Sections**  They contain the main contents of the file.

Load the PE file:

![](RackMultipart20200923-4-nfhana_html_b5143a6322664a3f.png)

As you can see from the previous screenshot, IDA Pro is able to detect the file type automatically.

Press &quot;OK&quot; and will be guided to the main interface:

![](RackMultipart20200923-4-nfhana_html_1836a88e41b796ec.png)

If you load a file, IDA will create a database &quot;_idb_&quot;. The database contains:

- **Name.id0**
- **name.id1**
- **name.nam**
- **Name.til**

The main interface contains  many views and windows:

This bar called &quot;the navigation band&quot; illustrates the memory space used by the binary

![](RackMultipart20200923-4-nfhana_html_614cacddba0ad08.png)

There is also a graph view to display functions as graphs and sub-graphs

![](RackMultipart20200923-4-nfhana_html_3689adc82b2c62c6.png)

**Functions Window: **

It lists all the recognizable functions by IDA pro

![](RackMultipart20200923-4-nfhana_html_4b62a2d06ad36a27.png)

**Imports**

It shows the imported libraries by the loaded binary

![](RackMultipart20200923-4-nfhana_html_1d3767d14acd1411.png)

The following is the text view where data is represented as disassembly

![](RackMultipart20200923-4-nfhana_html_c9be4c37ecb14df1.png)

You can find a lot of other available views: ** view -\&gt; Open Subviews **

![](RackMultipart20200923-4-nfhana_html_a25b53ebec1ae218.png)

To facilitate the navigation you can simply use the IDA shortcuts including:

Go to a new window: Alt+Enter
 Text: Alt+T
 Names: Shift+F4
 Functions: Shift+F3

You can find the full list here:  [Datarescue Interactive Disassembler (IDA) Pro Quick Reference Sheet](https://www.hex-rays.com/products/ida/support/freefiles/IDA_Pro_Shortcuts.pdf)

Based on its great capabilities IDA Pro is very helpful when it comes to Malware Analysis since it gives you the ability to extract many pieces of information including Strings (F21), imports, exports, graph flows and so on:

![](RackMultipart20200923-4-nfhana_html_fdffa22b11a7af75.png)

If you want to explore another great tool, I highly recommend you to take a look at my article:&quot; **How to Perform Static Malware Analysis with Radare2**&quot;

In this article, we did a high-level overview of IDA PRO
