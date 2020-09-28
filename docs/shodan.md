# How to perform OSINT with Shodan

In some of my previous articles we had the opportunity to explore different techniques to perform intelligence gathering including Human intelligence,signal intelligence, Geospatial intelligence and Open source intelligence. In this article we will dive deep into a powerful open source intelligence online tool called Shodan.

![](https://simonline.su/images/147.jpg)

## What is Open source intelligence? 

Wikipedia defines OSINT as follows:

> &quot;_Open-source intelligence is data collected from publicly available sources to be used in an intelligence context. In the intelligence community, the term &quot;open&quot; refers to overt, publicly available sources. It is not related to open-source software or collective intelligence&quot;_

Open source intelligence is like any methodological process is going thru a defined number of steps.In order to perform an open source intelligence you can follow the following phases:

1. Direction and planning: in this phase you need to identify the sources,in other words where you can find information
2. Collection: in this phase you will collect and harvest information from the selected sources
3. Processing and collation: during this phase you need to process information to get useful insights.
4. Analysis and integration: in this phase you need to join all the information and analyse them
5. Production, dissemination and feedback: finally when you finish the analysis you need to present the findings and report them.


## What is Shodan?  

![](https://static.shodan.io/legal/images/image1.png)

Shodan is a search engine that lets the user find specific types of computers (webcams, routers, servers, etc.) connected to the internet using a variety of filters. Some have also described it as a search engine of service banners, which are metadata that the server sends back to the client. This can be information about the server software, what options the service supports, a welcome message or anything else that the client can find out before interacting with the server.

You can use it by visiting the official website: [www.shodan.io](http://www.shodan.io/)

![](img/Untitled.png)

As a start, Shodan gives you the ability to start exploring some pre-selected search queries. Some of the findings are:

- Webcams
- Industrial control systems
- Databases
- Passwords and so on

![](img/explore.png)

For example, in the Industrial control systems section, you can search for

- XZERES Wind Turbines
- PIPS Automated License Plate Readers

![](img/ICS.png)

It supports many ICS protocols too.

Furthermore, you can use [shodan map](https://maps.shodan.io/) for more geo-centric searches

![](img/map.png)

Now let&#39;s explore how to perform some shodan queries.

To perform search, you will simply use the search bar in the main page

![](img/search.png)

To simpliest search form is typing the &quot;term&quot; you are looking for, like a website name, service or something and shodan will give pages of results that you can filter later

![](img/google.png)

Queries can be more specific. Shodan provides a list of advanced queries that you can use in order to get more accurate information. Some of them are the following:

To select a specific country type:

`country: <Country Symbol>`

For example, Germany code is: DE. So the query will be:

`country:DE`

![](img/DE.png)

County codes can be found here: [https://github.com/postmodern/shodan-ruby/blob/master/lib/shodan/countries.rb](https://github.com/postmodern/shodan-ruby/blob/master/lib/shodan/countries.rb)

To select  specific ports type:

`port: <Ports_HERE>`

For example:

`port:80`

![](img/80.png)

 To search for a specifit operating system(OS) type:

`os: <OS_HERE>`

