#  Detailed Guide: How to deploy your Elastic Stack (ELK) SIEM

Security information and event management systems (SIEM) are very important tools in incident response missions. Every security operation centre is equipped with a SIEM. In this article, we are going to learn how to deploy a fully working SIEM using the amazing suite the Elastic stack (ELK).

![](https://images.contentstack.io/v3/assets/bltefdd0b53724fa2ce/blt0a8f8d63938463bc/5d01b52bae9baaf01450ac67/introducing-elastic-siem-2.png)

Image source:[ dashboard](https://images.contentstack.io/v3/assets/bltefdd0b53724fa2ce/blt0a8f8d63938463bc/5d01b52bae9baaf01450ac67/introducing-elastic-siem-2.png)

In this article we are going to explore the following points:

- What is Elastic stack?
- How to install Elastic stack?
- How to install Elasticsearch?
- How to install kibana?
- How to install logstach?
- How to deploy ELK beats:  **Metricbeat**
- How to deply  **Auditbeat**
- How to deploy an  **ELK SIEM**

Before diving deep into the required steps to build a SIEM, it is essential to acquire a fair understanding of the different ELK components.

## What is the ELK Stack?  

![](https://assets.digitalocean.com/articles/elk/elk-infrastructure.png)

Image source: [ELK](https://assets.digitalocean.com/articles/elk/elk-infrastructure.png)

ELK Stack is the abbreviated form of &quot;Elasticsearch Logstash Kibana&quot; Stack. They are three open source projects. This stack is one of the world&#39;s most popular log management platforms by 500,000 downloads every month. The ELK stack is widely used in information technology businesses because it provides business intelligence, security and compliance, and web analytics.


Let&#39;s get started;

To build the SIEM, you need to install the required libraries and programs:

For the demonstration, I used a  **Ubuntu 18.04**  server hosted on Microsoft Azure

Update the sources.list file:

`sudo apt update`

![](RackMultipart20200926-4-122n7kb_html_a3e131f7d91263a.png)

Install Java JDK 8 (and _apt-transport-https_ if you are using Debian)

`sudo apt install -y openjdk-8-jdk`

![](RackMultipart20200926-4-122n7kb_html_368905f391c68594.png)

Check the Java version with:

`java -version`

![](RackMultipart20200926-4-122n7kb_html_29ea21525978abbe.png)

Now let&#39;s install Elasticsearch:

![](RackMultipart20200926-4-122n7kb_html_ef1561cc1b298c9f.png)

`wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -`

`echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list`

`sudo apt update`

`sudo apt install elasticsearch`


`sudo apt install elasticsearch`

![](RackMultipart20200926-4-122n7kb_html_a7b1fbcbe1b99b48.png)

After installing elasticsearch you need to configure it by modifying  **/etc/elasticsearch/elasticsearch.yml ** file

`sudo vi  /etc/elasticsearch/elasticsearch.yml`

![](RackMultipart20200926-4-122n7kb_html_6963ce1b4b537ab2.png)

Un-comment  **network.host**  and  **http.port**  and assign values to them. Don&#39;t use &quot;0.0.0.0&quot; in your production servers. I am using it just for a demonstration.

save the file.

To start Elasticsearch on boot up type:

`sudo update-rc.d elasticsearch defaults 95 10`

Start elasticsearch service:

`sudo service elasticsearch start`

Check the installation:

`curl -X GET "YOU_IP:9200"`

![](RackMultipart20200926-4-122n7kb_html_80868b75efeae6fa.png)

Now let&#39;s install Kibana:

![](RackMultipart20200926-4-122n7kb_html_8282e73a606e5475.png)

`sudo apt install -y kibana`

![](RackMultipart20200926-4-122n7kb_html_41fb492ef379d917.png)

And like what we did with elasticsearch we need to configure it too:

`sudo vi /etc/kibana/kibana.yml`

![](RackMultipart20200926-4-122n7kb_html_3a323235e05795d2.png)

Un-comment and modify the following values:

    server.port: 5601
    server.host: "YOUR-IP-HERE"
    elasticsearch.url: "http://YOUR-IP-HERE:9200"

Save the file, and perform what we did previously

`sudo update-rc.d kibana defaults 95 10`

 and run it:

`sudo service kibana start`

Now go to [**https://YOUR-IP-HERE:5601**](https://YOUR-IP-HERE:5601/)

Voila, you can start exploring the dashboard of some pre-installed Sample Log data: ![](RackMultipart20200926-4-122n7kb_html_b6dae142943594d3.png)

![](RackMultipart20200926-4-122n7kb_html_90c8066d5a1a6c61.png)

Install  **logstash**  to collect, parse and transform logs if needed:

![](RackMultipart20200926-4-122n7kb_html_deec5e4f8cbb0f66.jpg)

`sudo apt install -y logstash`

![](RackMultipart20200926-4-122n7kb_html_5426d067add6fb5c.png)

But wait how can we use our own data?

It is a good question, we can receive data from a host using what we call &quot;Beats&quot;. You can find the full list here:

As a demonstration i am going to use &quot;[Metricbeat](https://www.elastic.co/products/beats/metricbeat)


`sudo apt-get install metricbeat`

![](RackMultipart20200926-4-122n7kb_html_964e6e7f8f2e763b.png)

Configure the beat by typing

`sudo vi /etc/metricbeat/metricbeat.yml`

To start metricbeat on boot up type as usual

`sudo update-rc.d metricbeat defaults 95 10`

Start the beat:

`sudo service metricbeat start`

Now go to the main dashboard and create a new index:

If everything went well you will see your beat:

![](RackMultipart20200926-4-122n7kb_html_17363eb655e2f8b6.png)

Select the time filter by selecting @timestamp:

![](RackMultipart20200926-4-122n7kb_html_653b995d7b2bece2.png)

Then, you can visualize any data you want from that beat.

By now we deployed the most important parts. Let&#39;s learn how to deploy the ELK SIEM:

Go to the sidebar and you will find SIEM option:

![](RackMultipart20200926-4-122n7kb_html_1644059ad434fb8c.png)

It will take you to the main SIEM page:

![](RackMultipart20200926-4-122n7kb_html_cd9bb12ade71e7d7.png)

But now we need data to run the SIEM. In order to do that we need to install other beats from sources like the following:

![](RackMultipart20200926-4-122n7kb_html_3518c7fd9c74aa6c.png)

For the demonstration i am going to use the &quot; **Auditbeat**&quot;:

`sudo apt-get install auditbeat`

Configure it by:

`sudo vi /etc/auditbeat/auditbeat.yml`

Check the setup:

`sudo auditbeat setup`

![](RackMultipart20200926-4-122n7kb_html_7fdadf4d6ffc9ce2.png)

Run the beat:

`sudo service auditbeat start`

If you did everything correctly you will see this on the SIEM Dashboard:

![](RackMultipart20200926-4-122n7kb_html_aae8a38d3b9d4c5.png)

Congratulations! Now you can see the dashboard of your SIEM.

![](RackMultipart20200926-4-122n7kb_html_f93d6ec7f1dbf4aa.png)

Check the hosts:

![](RackMultipart20200926-4-122n7kb_html_1e1df9204c352d21.png)

![](RackMultipart20200926-4-122n7kb_html_dbcdc17289a48711.png)

Check the Network Dashboard:

![](RackMultipart20200926-4-122n7kb_html_2a770803c198215.png)

A system Overviews:

![](RackMultipart20200926-4-122n7kb_html_62736cd00bc9744.png)

![](RackMultipart20200926-4-122n7kb_html_32d1d3a50de1ef25.png)

Voila, you learned how to build an ELK SIEM.



