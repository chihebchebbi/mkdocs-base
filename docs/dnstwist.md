# Azure Sentinel: Using Custom Logs and DNSTwist to Monitor Malicious Similar Domains

In this article, we are going to explore how to monitor similar domains to yours, in order to protect your users from being victims of social engineering attacks.

When performing computer-based social engineering attacks such as phishing, attackers buy similar domains to yours in order to trick your users. This is why keeping an eye on similar domains is essential to avoid such attacks.

First we need to find these domains. One of the tools that helps you to generate similar domains is &quot;DNS Twist&quot;. You can find it here: [https://github.com/elceef/dnstwist](https://github.com/elceef/dnstwist)

According to DNS Twist developers:

> &quot;DNS fuzzing is an automated workflow for discovering potentially malicious domains targeting your organisation. This tool works by generating a large list of permutations based on a domain name you provide and then checking if any of those permutations are in use. Additionally, it can generate fuzzy hashes of the web pages to see if they are part of an ongoing phishing attack or brand impersonation, and much more!&quot;

![](https://lh3.googleusercontent.com/ufs4QeX_177Vig6KbkCfCDYQr0zraToJmtP-xT8v3tYKCaq6f1aDNKi7LS0v6ITg6e1AQyby5IWFuYtrjsttIQ3qvPlN2vuq9nc5mgl2P8g4_4FHcZtpFPjDfQ3aNnsxqc04AO3o)

You can even try to generate some domains online here: [https://dnstwist.it](https://dnstwist.it/)

In this demonstration, we are going to use python on Windows to generate similar domains:

Type the following command to install the python module:

```
py -m pip install dnstwist
```

![](https://lh5.googleusercontent.com/drKtiAxdyyDrAJYzT4OGg4pfsL-nDHF13elog6AhBYMQ4NhVj9n7NbWwTnIma4EEl91aHaK6FJo7br6EMxaWkp_3iOXAruECnfm9SVM83ZAHeClR9rjIHPOBGOQyE_4kc2i32eBL)

To generate similar domains, open python terminal and type:

```
import dnstwist 
fuzz = dnstwist.DomainFuzz(“<YOUR DOMAIN HERE>”)
fuzz.generate()
fuzz.domains
```

![](https://lh5.googleusercontent.com/3-m4vfiYqxqynl8Jgp4yFy70R_-tBTe9AspSEkzuZO0svONObXGSat253K1wa4BA8cCdG_KpgKfpYXQw8h7QLs43KHg2BMbVkI3IojvLtrckm0I_2FYEQS-wt_vd119ZBIZ_yGGW)

For example these are some similar domains to &quot;google.com&quot; after parsing only the domain names:

![](https://lh5.googleusercontent.com/lPnRXC7a9o1lnrbGpHvW_lekpDa-T0hQmBraPfTwfryq4dQYVj4VUG8nYfMJmMUO1SIXC9tEWe1DWne2RLMyvmOQgN3Q0z3xkRPRXo6Wizx6-Ruv-NKXoj9dYHlwt5IDWHfFd7fW)

You can also use this API: [https://dnstwister.report/api/](https://dnstwister.report/api/)

![](https://lh4.googleusercontent.com/4BjqjrEmh09unHRcsl4q2VDtpun4s8ggrTIRyxMte_VlEsjnbupnJKfhlfr2fnLnjmJpQiUWvjiwbO15hn0HFLuX1o9e40eRpNcwd2YeC7OC6a9zs-NxNsCoZS4Qh-klqbdkT2y8)

To store the similar domains you can build a small script to achieve that. For example the following snippet stores similar domains in a file called &quot;Similar-Domains.txt&quot;

![](https://lh4.googleusercontent.com/c1gD2x0YzhIcQD7i0IfopshTUFLsMsRWpvVky2tOPlSUBkDxMOuPJjXbp1r7XMMH8jKq6mdQq5jh4vezexVtLplLlWQWyX8bArhB5G2KC2ZfhE8CqRzleyuGOtavGJCBzDN9NbQT)

![](https://lh4.googleusercontent.com/6P5RLV-cZ_BZo8JUcaVTLKMe--BsUc7MKF7S9D7UgmKx-RYT4M_GZbRnFDnnGpVUypzDd8mrA6zz5cKQ_zzXzC35TM9e1X6GxcPoKNTQbxmEquQ8tDkwtzq5mXAvwcHBCcsWucw2)

Once, we have a file that contains the similar domains, now we need to send them to sentinel so later we can create rules based on them.

Go to &quot;Custom logs&quot; sections and upload a log sample (a snippet from your similar domains file)

Select the limit delimiter: New Line

![](https://lh3.googleusercontent.com/zsiXd9SubLEM859fb5rbBWy_foIstDf0gcUG-JqzQJieKIqRflAKJ6KTLnKqWuR3IVYvb-diZtHDSfNxknCvIaCEDpw_XVrzmcgyZ3IIZUdatI0pZSumEA7odh_XCghHus17f0n6)

Add the file path. In my case &quot;C:\Users\Computer\Similar-Domains.txt&quot;. If you have many log files you can use regular expression such as \* eg: C:\Users\Computer\*.txt

Add a name and description to your custom log source

![](https://lh6.googleusercontent.com/X4gDlkB4NzP7xcTHCKYRKrSnu4QtAlIKsR8QZxaNVToDqCz4Qs9ubjhS49QV2AHeHHddsr2bSPfhYEObQx4vqLQgHey3Dyml3d2WvbMG48PWwfCrmIwOr_o2RLxdw7PKfXX1IMH3)

Voila! Your custom log is created successfully

Go to Sentinel log section and you will find it under **Custom Logs**

![](https://lh4.googleusercontent.com/A4--3b9yA14JKO5-FQkLpHkdBa_5FU-PlrJe1NlYQkP92WPIfm6GjZyh9nZv_9d3SGxI7tgnboi8eSpStNJg1A3PdKjwC-FKtXJ3oGGWP1lmXIVQL0QeaVNivDLpa17cjxSe759g)

To query it, simply select its name as follows:

![](https://lh6.googleusercontent.com/P-MVOivZsdCIMuqtS-77O3AoeQqFIDhzTV9YZVkp43lQcXo5qvW8Yx5ivfNuWEiyK3mNxvXgIEHxa7sZ2x4RrXF3SefPrV0bQ2MRDNlJ5dAwj5pLmO-ZRf2iRdd7UsLaY_educXk)

Finally, now you can create a rule to detect if a user visited one of the similar domains. For example, you can use the [JOIN](https://techcommunity.microsoft.com/t5/azure-sentinel/azure-sentinel-correlation-rules-the-join-kql-operator/ba-p/1041500) function with [DNSevents](https://docs.microsoft.com/en-us/azure/sentinel/connect-dns) source.
