# Azure Sentinel: Process Hollowing (****T1055.012****) Analysis 

In this article, we are going to explore a technique called &quot;Process Hollowing&quot; and how to detect it using Azure Sentinel.

Before jumping in the detection part, it is essential to explore some important terminologies.

According to [MITRE](https://attack.mitre.org/techniques/T1055/012/):

![](https://4.bp.blogspot.com/-oP3fsd9IyWg/XIF6kIC4xDI/AAAAAAAAEVs/d2ObvQoSKTQffYTiKX2H69CWvIYLuaXvACLcBGAs/s1600/attack.png)

&quot;Process hollowing (T1055.012) is commonly performed by creating a process in a suspended state then unmapping/hollowing its memory, which can then be replaced with malicious code. A victim process can be created with native Windows API calls such as CreateProcess, which includes a flag to suspend the processes primary thread. At this point the process can be unmapped using APIs calls such as ZwUnmapViewOfSection or NtUnmapViewOfSection before being written to, realigned to the injected code, and resumed via VirtualAllocEx, WriteProcessMemory, SetThreadContext, then ResumeThread respectively&quot;

![](https://lh6.googleusercontent.com/X7bS6yaiRtrnC9B1zO4xN1rMbCfzZnBOS-94MwBilbXPwdGdPXG2lQMk1RpSTvkzCyAwsyZEdQV8J5gAgqDX_IB8KSY5W1Q7mO4NnwPEmvrSnWc_TmXMQ4YJA9hJAd1w3ojxo2RV)

To learn more about Process hollowing, i highly recommend you to check this piece from Elastic: [https://www.elastic.co/blog/ten-process-injection-techniques-technical-survey-common-and-trending-process](https://www.elastic.co/blog/ten-process-injection-techniques-technical-survey-common-and-trending-process)

This technique is widely used by adversaries such as Duqu and TrickBot

![](https://lh4.googleusercontent.com/RuGwhJNJ2jecJMALsGYeNxywIm_7Kl4QCTbWFOT9fDGcCCLLteWamrXov0GWbPI4YABnsPxmvFJwuLzD7cApwgCC1MfpGMRywzQivhiJI9TE0RgYEuXjEcIdDIfWiAU0mKCXSe1w)

The following pieces by [Jonathan Johnson](https://medium.com/@jsecurity101?source=post_page-----c11f5aedf5e0--------------------------------) and [David Polojac](https://medium.com/@david.polojac?source=post_page-----b6014a83d4c8--------------------------------) from Specterops deep dives into the detection engineering aspects of process hollowing

- [Engineering Process Injection Detections - Part 1: Research](https://posts.specterops.io/engineering-process-injection-detections-part-1-research-951e96ad3c85)
- [Engineering Process Injection Detections — Part 2: Data Modeling](https://posts.specterops.io/engineering-process-injection-detections-part-2-data-modeling-c11f5aedf5e0)
- [Engineering Process Injection Detections — Part 3: Analytic Logic](https://posts.specterops.io/engineering-process-injection-detections-part-3-analytic-logic-b6014a83d4c8)

For the detection we are going to use Azure Sentinel and sysmon. Sysmon can be downloaded from here:

[https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon)

To install run the following command as administrator:

sysmon.exe -accepteula -i \&lt;CONFIG\_FILE\_HERE\&gt;

You can use the following config file by ION-STORM

[https://github.com/ion-storm/sysmon-config](https://github.com/ion-storm/sysmon-config)

To explore sysmon events, use Windows Event Viewer: Applications and services logs -\&gt; Microsoft -\&gt; Windows -\&gt; Sysmon -\&gt; Operational

![](https://lh6.googleusercontent.com/nomqR-Kapysj6uPyBnhAZL4Obi_P0iC3ZVROxeMV-uQo3sWeJd-Osfa-robi2JpIC9PT4AyPwmAOucqFdMKd59EiR15eKK4o1x09n7qf46lDSuSpLb4i8OxD0FeGwraxL9UUOUx6)

To send sysmon events to Azure sentinel, deploy a new connector (Security Events) to start with Windows Event logs

![](https://lh4.googleusercontent.com/Tvd5p9EZDAollURzAJtnnav01ZoKEqwYCZ71LVlYLe4NTYucn3O5MJnvfUmX8jVZ6XpFZ6KydVoVXx5_8prS_2uPOyMMlNByZau4AN5DbUz2J9lKF07r-ReSgV162n6LcLhbZhco)

Install the agent.

![](https://lh4.googleusercontent.com/IWPdgN0gEhguY0ux5IDy5rp1_fOForm-FBqN0Dollw7NyUoe3w-j5XLxIUWcuK87IakPLGwN44YI_5euT1Dsjf56z8w6kIBegBtsfhcjFapvKp9mQlanBpMsfdRim2xFHHyYAN8P)

Now go to Settings -\&gt; Workspace Settings -\&gt; Advanced settings -\&gt; Data -\&gt; Windows Event Logs and add the following event log name: **Microsoft-Windows-Sysmon/Operational**

![](https://lh5.googleusercontent.com/gxN8UqDk76wKOzA6CWOyzJ2V64vbuVtrLs8eWFW39JLoqkDG3g-yhDFb-NadSChiEP7FCSp3cJV-6BNJac8WJVFbINLD0zkEkdDOQ6VER0WRD8VKvSmN2XdIwqOVz4-QaPVDW6eu)

To check the events go to Azure Sentinel **Logs** section and run the following query:

Event

| where Source == &quot;Microsoft-Windows-Sysmon&quot;

![](https://lh6.googleusercontent.com/XjLdqsr7KShVhpQ9OCUp5Yg8O2t3_O5IG5JegrnfrzLV2P1Bqu1bkUSQLvGNo9lFXiUjxZjxO3PCgjr80ngnWveDxzqCUEhLbhyivO2DxM1xKUz4JCd0xuQ8J-AOQOIWNJQo4Lqz)

As you will notice the EventData fields are not parsed and filtered. Thus, it is recommended to use one of Azure Sentinel sysmon parsers: [https://github.com/Azure/Azure-Sentinel/tree/master/Parsers/Sysmon](https://github.com/Azure/Azure-Sentinel/tree/master/Parsers/Sysmon)

![](https://lh5.googleusercontent.com/Ubnd00yDybgQhN4JhECDR7fwpc9-zs0nPGmNgpmWd9cQZ3LusfM1WeQe4yGjfojoHhANBxv6p9AD1Qf_K6zRGC273yVzqI4_GwIgrNIWnNvvfceIAOCeQufDG8DYgqkoE6IUr-Zf)

To use the parser, copy the file content in log analytics and save it as a function (e.g Sysmon\_Parser). Now the events are well parsed:

![](https://lh6.googleusercontent.com/IKy1Y1uOCXUNVB-5R276SrpDvIA1RYieufwVrnTLu5pIwCcZ90e0cO51NVuaTGxdB-TUNb0V8HmCCiH8GyT4JQMImBIL9rCpWwSV_xz17pY5nCzVQVAxXSTI2ND-fszex99sqFxg)

To correlate APIs with Events, a mapping phase is needed for a better visibility. Thankfully, you can use these sheets:

- [https://github.com/hunters-forge/API-To-Event](https://github.com/hunters-forge/API-To-Event)
- [https://github.com/jsecurity101/Windows-API-To-Sysmon-Events](https://github.com/jsecurity101/Windows-API-To-Sysmon-Events)

![](https://lh6.googleusercontent.com/gXtrunz7-rk0fn4QsWZexS79FDKzcgTksnRcDcZ-qMvt3boRMrkfLmcCZj4B5_oa1ay4BU48eMNj7OvO2x18aolUUpwGwzVRE4cMXjW7ItCbQBC1UObGtxwch7avLg_61MWGrOb6)

More details about mapping can be found here: [Uncovering The Unknowns](https://posts.specterops.io/uncovering-the-unknowns-a47c93bb6971)

Now we know what sysmon EventIDs to watch

![](https://lh4.googleusercontent.com/iZSX5y0Ic6DEpLNv7AP36oERLaHjDaisp8uFgu_0yAy9kRmL3PyDoleP9MikrWDEOm2ouDiq4_9Sz741ECS_LHMCReMaKzjZsuoeeVkmw-fWF4Tn0qgIuFhwdtBcOaREXGb8TU4E)

Let&#39;s perform a process hollowing technique using the following poc: [https://github.com/m0n0ph1/Process-Hollowing](https://github.com/m0n0ph1/Process-Hollowing)

![](https://lh5.googleusercontent.com/xZlFmxGAXQat_msKYQ2-4ByHIr3DIkd9aRSckv5DPF8irFhsOvykbDq6xD_HthAvI080pIB7nXw7MkF9F9nkBRphs-ivCF4soxv_qpFPokjdieB_Nto6bQ10yK8hk1LYKLixksT2)

Go to Azure Sentinel logs console

Sysmon\_Parser

| where EventID in (&quot;1&quot;,&quot;10&quot;)

| project SourceImage, TargetImage, EventID, GrantedAccess

- EventID 1: Process Created
- EventID 10: Process Accessed
- The [project](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/projectoperator) operator: Only the columns specified in the arguments are included in the result.

![](https://lh3.googleusercontent.com/Nev_uSPrZ2oD_az_eEMTSjDglOFteNdA-XDhJZEAwbLkzUfmbun_gU25OY6bNnNLE0aYovnVjI9rDQbQIp4wtn5QrIJS5ekTb6vUHC0reNZZsPwOooIunGbE3Iw5Pb3XTORsCIc6)

In our case, the access rights used by the POC is 0x1fffff which is [PROCESS\_ALL\_ACCESS](https://docs.microsoft.com/en-gb/windows/win32/procthread/process-security-and-access-rights?redirectedfrom=MSDN) even though according to [Jonathan Johnson](https://medium.com/@jsecurity101?source=post_page-----c11f5aedf5e0--------------------------------)&#39;s research process hollowing only needs the following rights:

_PROCESS\_VM\_WRITE_

_PROCESS\_VM\_OPERATION_

_PROCESS\_SUSPEND\_RESUME_

_PROCESS\_CREATE\_PROCESS_
