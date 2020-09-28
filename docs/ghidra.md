# **Getting Started with Reverse Engineering using Ghidra**


 In this article, we are going to explore how to download Ghidra, install it and use it to perform many important tasks such as reverse engineering, binary analysis and malware analysis.

   ![](https://lh5.googleusercontent.com/UhJXUqLIY7mgZkxEUGAPtW2ICyO0VF4TbwJ4Soa2_EtFxBdoiAeODnUEyfaAcBo_GfScvyLIHG8ZfZTb9BnR-VC4VCtltzwNsNULPw8wU61WotiABvb6Ns4qFR_s60SX8-FuvSI)

[Source](https://www.bleepstatic.com/content/posts/2019/03/06/Ghidra_headpic01.png)

But first what is Ghidra exactly?

<img src="https://lh5.googleusercontent.com/TmgOszGWkRqttmJ379gcglZAxiuooMbvVZ_ZLkdULKYNpnhdxKiIpZQX-n2perJs7ElXzbi9R8QZMQUv4V8qfn9vQloemzvlI_sGXGtoiFYdHhoRat9n9T1GlYQux0CUgts6-TQ" width="200px">



According to its official [Github repository](https://github.com/NationalSecurityAgency/ghidra):

&quot;Ghidra is a software reverse engineering (SRE) framework created and maintained by the [National Security Agency](https://www.nsa.gov/)Research Directorate. This framework includes a suite of full-featured, high-end software analysis tools that enable users to analyze compiled code on a variety of platforms including Windows, macOS, and Linux. Capabilities include disassembly, assembly, decompilation, graphing, and scripting, along with hundreds of other features. Ghidra supports a wide variety of processor instruction sets and executable formats and can be run in both user-interactive and automated modes. Users may also develop their own Ghidra plug-in components and/or scripts using Java or Python.

In support of NSA&#39;s Cyber Security mission, Ghidra was built to solve scaling and teaming problems on complex SRE efforts, and to provide a customizable and extensible SRE research platform. NSA has applied Ghidra SRE capabilities to a variety of problems that involve analyzing malicious code and generating deep insights for SRE analysts who seek a better understanding of potential vulnerabilities in networks and systems.

[https://github.com/NationalSecurityAgency/ghidra](https://github.com/NationalSecurityAgency/ghidra)

![](https://lh6.googleusercontent.com/Pt6epOt74FM6QlmW37KHcRRrKqo81LCGX2jOKOuInF1GbznU8vOrsC2A9Tt_kQYkipY4uXOW0m55H0tbVlToTWjhJo5cFP9deqw4ZXCGqrzlHptbfxaVtANYn1AjTROH8zgUPGY)

The official website of the project is [https://ghidra-sre.org](https://ghidra-sre.org/):

As you can notice from the official description that this tool was developed and maintained by the US NSA (National Security Agency) which leads us to think about if this tool is secure. Check this post if you didn&#39;t know what i am talking about:

### Compilation example with a C Program:

Before diving into the fundamentals of reverse engineering with this powerful tool (Ghidra) , let&#39;s explore the compiling phases in order to get an executable and some important terminologies.

[Wikipedia](https://en.wikipedia.org/wiki/Reverse_engineering) defines Reverse engineering as follows:

&quot;_Reverse engineering, also called back engineering, is the process by which a human-made object is deconstructed to reveal its designs, __ __ architecture __, or to extract__   __knowledge__  __from the object; similar to scientific research, the only difference being that scientific research is about a natural phenomenon.&quot;  _

**Compilers:**   convert high-level code to assembly code

**Assemblers:**  convert assembly code to machine code

**Linkers:**  take the object files in order to generate the executable

**Disassemblers:**  convert machine code to assembly code

The phases are represented in the following graph:

![](https://lh6.googleusercontent.com/csWoTaoDqTphcdydrm3LIrY4qUdjl7L66LsolU_aC7lcc8Bjw7LlmsJ2oOYrh3FmA45oHWX18KiIf36ZR2v_MtFYGUGb-dNtBjj3jDnN5rafS0x8BdUl5RMRccQGnwFoL29OXmo)

[Figure](https://miro.medium.com/max/518/1*wHKe6W4opLmk6pb7sxZz6w.png)

As a demonstration, let&#39;s compile a simple c program. The most known easy program is simply a &quot; **hello world!**&quot; program

Create a  **hello.c ** program:

    #include <stdio.h>
    void main(void)
    {
        printf ("hello world!\n");
    }

Now let&#39;s compile it and link it  with gcc

`gcc -o helloWorld hello.c`

Run the executable

`./helloWorld`

![](https://lh6.googleusercontent.com/E50ujmhp_jn_YPliSGQQ7cNwuynIgEOp1MkEoX7L4BD5vwSWGUN5ns8z8gvW7WD33pl_xt9lpG-TB_GaA3x0mU50sBIcJ7AuDwZ1iv71rAy5Xm3S3k_kHpFBOC4U0kfLdx1qUtc)

**How to install Ghidra? **

To use Ghidra we need to install it of course. As technical requirements, you need the following

### **Hardware**

- 4 GB RAM
- 1 GB storage (for installed Ghidra binaries)
- Dual monitors strongly suggested

### **Software**

- Java 11 64-bit Runtime and Development Kit (JDK)

Go to [Download Ghidra v9.1](https://ghidra-sre.org/ghidra_9.1_PUBLIC_20191023.zip)

Download it and  install Java JDK

Go to the installation folder and run the Ghidra bat file

![](https://lh5.googleusercontent.com/RPew3jermK8UCQbBLR8_01SmQl1DnU3yfIN4ah_wKO_A1qQP5QGBGYoiJ_ih4XVmllbL1ck0wtYDNDuheW5Rw5q3h3973iv3qvow4zNnp1cLoDqvYKdVVG7p8wScc3RDQoIChdM)

![](https://lh5.googleusercontent.com/3mLJUF0MvS-tkBcJvZT72srQSefCDNwQ2r6L_rfG5HcIQT_uhnOddZu92ggD18uno4hLOoXMYWRRYFUCFzXYEvx-i1viZ8XPBZ7QxGV1p34THPnGC0tLMi__RDHlVc1zgb0GU38)

For more information about the installation steps you can check Ghidra official documentation: [https://ghidra-sre.org/InstallationGuide.html](https://ghidra-sre.org/InstallationGuide.html)

**Reverse engineering example (CrackMe Challenge): **

We learned the compilation phases in order to generate a fully working binary. Now it is time to continue our learning experience with acquiring some fundamentals about reverse engineering. That is why we are going to download a small and easy CrackMe challenge and we will try to understand what is doing and how it works in order to find the correct password to solve the challenges.

The challenge that we are going to solve is a part of this free and publicly available training materials: [https://github.com/Maijin/Workshop2015](https://github.com/Maijin/Workshop2015)

We are going to follow [Here Be Dragons: Reverse Engineering with Ghidra](https://www.shogunlab.com/blog/2019/04/12/here-be-dragons-ghidra-0.html "Here Be Dragons: Reverse Engineering with Ghidra")

Download the GitHub repository, go to /IOLI-crackme/bin-win32 and you will find the challenge binaries.

![](https://lh6.googleusercontent.com/CMQl936R3s5qBARYKXH7HHhwAtIjCMRC6SXf9dXv8khalHY_gPyhKHPd0VUF6d22J67rEPwFga2y4gsBc9DNMzYZDO6bPrSUfwhmlx3qlBLTbImORFf984zELmBL5QrOV8VpfZ0)

We are going to reverse &quot; **Crackme0x01**&quot; file.

Let&#39;s open it directly using the command line terminal:

Enter the binaries folder and type:

`Crackme0x01.exe`

Enter a random password. In my case I entered &quot;root&quot; but i get an &quot;Invalid Password!&quot; error message

![](https://lh4.googleusercontent.com/fi7D1PemvtCPrGujiQm3_ros6pqNlYJxTNlwZutgFVHm3KPRwNPm5UgLsqPbonrcYLHSbLAComQI80WEkk7dBbpDM9Y0xc8Hp1XqvuhDmbUkZK_dglTsD0N38CkTQ9fCmw0IEjs)

Then let&#39;s crack it

Open Ghidra

![](https://lh4.googleusercontent.com/_e9S4pmjACgSyW_ixmfs4hvzFDFGbkCE_A_wMRBiqc81QSDZaidX-fyZ2_uWclaIyQr5YDYpllhpzC0Qv_gJuA66mJrTjL6ReTXanXjZaYGg3j41PhyW86MPdSozS5vEMF0FIpQ)

Start a new project:

![](https://lh5.googleusercontent.com/KYCrv6Zn4fwJlNFVNyRjBgCwg7wBoIt3zM5k7_wwFbxHHB31S2L2wgSOI6vWxrSV8PjuVjfkQ26piOa_1oTElCKgZkE51cWG47nLeUS9-f_iTnZj1yCOYnXR1iUt70I6nYgIcdM)

Name the project

![](https://lh6.googleusercontent.com/FV9a4Go5QD5baxtw6Avdfwmh9xtwuILzlGy1i14l7_vLBD2H0M3QXb0HDnbhBLMqJ1abxh3gKvhbKakY9Qi7BOhulOi2uFxizCtOoBpJI6arwPtoiqsPW_6D9updORQiGubwh54)

Import the binary with  **Batch Import**

![](https://lh3.googleusercontent.com/_jepMvOjKWazMPJWj4kxu2TEVPr9bDZbWnkoSnMM0nmS7hu74ywXViNou97ItzM3Xv_oDOF_5a5aeQgrSzD6_ZN5NFj0xARcmflg-uK9y5nAeTSqZ8U9ckkAELSFtFrGMlbWAIQ)

Open the binary

![](https://lh4.googleusercontent.com/8qTrBjincCOBiGzIDrl_fgMkU-7RTgwNzZ7WeHuj2YiOdI7happEmUhJkztER6TDcV-a_t0R6D3XTe2sYvxudNjFyhTMHI6k0uTXo7fY3620viY2XwFppsWbwJKvDoinjxTwaNw)

Select the required options and click &quot;Analyze&quot;

![](https://lh3.googleusercontent.com/wboOWEeylhvfRQ0HBm3FsCLpg-uMemAzWdw_wwyS1sq36qEQXk4bO7_nq6YkNn_2AQQb3An-vg3u1C12VVCq8N5PBHYD-ni4eYpLh-5kzAyCM6KxUpxZVU-ty_WItPOPNizymFU)

Voila! This is the main windows of Ghidra

![](https://lh3.googleusercontent.com/mXjD-3ffYx6f-j63Rfpt6UP7Jd2xKc5LUitRuqzFHucG0YjCnQf2PrmjCYCe1ufNh2oNAwKHpuChBdC1TOoQEOCr_Xlv-oOPUBP2DupMXC0ukfJDQJtxAvcaihCzU1Kc3eKcChs)

You can also check the function graphs

![](https://lh4.googleusercontent.com/EZFHl8JmaXgfCu5yjZrooo_RIhXVDIKh8SUykGot1ACwwnnsxR_EE5K-OqjanBZCeEbSWxtIZwF6yyQ0ah6FJsolPrMojV8Oe_w72e5hfjaTn9Op6hBV4j4Rf8gw20wbj3cyVY0)

To solve the challenge let&#39;s first start with extracting the binary strings

![](https://lh3.googleusercontent.com/lvBkPKquYS5DE5mwbR4QSNUD4dSpiroCBSA3OMjFgWJdJj6NhclIaLMBuzQx9seCzT189nmzdakHEOYh9oS6G7-rXxyLFKdlRJ5qcFaXhqf2q3JmjhCP6jDBhmUGwy4cDtom4fQ)

As you can notice we get all the strings of the file. One of them is &quot;Password OK :)&quot;

Ghidra is powerful. It gives you the ability to decompile the file. As you can see from the screenshot it is giving us a readable code.

If you check the code carefully you will notice this line of code

    If (local_8 == 0x149a)  
 
        _Printf ( “Password OK :) /n ”)

At the other side of the window you will see the CMP instruction. With a small Google [search](https://www.tutorialspoint.com/assembly_programming/assembly_conditions.htm) you will find that

&quot;_CMP is generally used in conditional execution. This __ _ **_instruction_** _ __ basically subtracts one operand from the other for comparing whether the operands are equal or not. It does not disturb the destination or source operands. It is used along with the conditional jump __ _ **_instruction_** _ __ for decision making. &quot;_

![](https://lh3.googleusercontent.com/pKlug5j8ahmIhCF11PdA3yawQ_Y67PMCScmbU9dBmAL9rhm3uJ_L1WyevwsZ5IUH0BiqDjdY-YbNyQB286R_8KHGN6ratHhopAhIkGKXFaLtu5i0ir-ctpkEv981cpbMux0b9p0)

Then if our analysis is correct then the valid password will be a conversion of &quot;0x149a&quot;

To check its value double click on it and you will get this.

![](https://lh5.googleusercontent.com/O3IWhjuyeW3vnxI-YZybqArV1n-7JiFm34W-O0yILJcZCOCUIFtKyKe5VOLh4UtjqWxS79jNgoUhZd_zS5xzrsGmITpVVm0nnUT3n6WlGGfGOy32yL2r1hNU-9GYkXvcznjP-0E)

The decimal value is &quot;5274&quot;. So let&#39;s try it:

Go back to your terminal and run the binary and this time type 5274:

![](https://lh3.googleusercontent.com/OLmwmbztPOW5Q8KDF4lHmqmQKl3ZYjTxZdecmJUixX9_hoUqaYYZ33jvUj1sYSvbte-Vc9tN0kJKvdHvIx_9leUwZ7MmftjTgeasTKUxSk97dSP7mw2OKNo9oodB2nkTJIvlHpw)

Congratulations, you solved your first  **crackme**  challenge.

This article will be updated with more interesting sections in the next few hours like Malware Analysis with Ghidra

**Further resources **

- [https://ghidra-sre.org/CheatSheet.html](https://ghidra-sre.org/CheatSheet.html)

**References **

- [https://www.tutorialspoint.com/assembly\_programming/assembly\_conditions.htm](https://www.tutorialspoint.com/assembly_programming/assembly_conditions.htm)

**Summary **

This article was a good opportunity to learn the fundamentals of reverse engineering with an amazing tool called &quot;Ghidra&quot;

