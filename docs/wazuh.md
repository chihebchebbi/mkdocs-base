# **Hands-on Wazuh Host-based Intrusion Detection System (HIDS) Deployment**

Hi Peerlysters,

In this article we are going to learn how to deploy a powerful HIDS called &quot;Wazuh&quot;

![](https://1.bp.blogspot.com/-cLWhyj0UdO8/Vqvp68xMPHI/AAAAAAAAHA4/c1NJZ803AaE/s1600/WazuhDashboard.JPG)

_[Image Source](https://1.bp.blogspot.com/-cLWhyj0UdO8/Vqvp68xMPHI/AAAAAAAAHA4/c1NJZ803AaE/s1600/WazuhDashboard.JPG)_

## What is an intrusion detection system?

 Intrusion detection systems are a set of devices or pieces of software that play a huge role in modern organizations to defend against intrusions and malicious activities.We have two major intrusion detection system categories:

- **Host Based Intrusion Detection Systems (HIDS):** they run on the enterprise hosts to detect host attacks
- **Network Based Intrusion Detection Systems (NIDS):** their role is to detect network anomalies by monitoring the inbound and outbound traffic.

The detection can be done using two intrusion detection techniques:

- **Signature based detection technique:**  the traffic is compared against a database of signatures of known threats
- Anomaly-based intrusion technique: inspects the traffic based on the behavior of activities.

## How to Deploy Wazuh HIDS?

![](https://d7umqicpi7263.cloudfront.net/img/product/caf0ea2f-b328-49c7-a793-f3c32cfa01df/5235ce4f-f702-4584-b507-727817ab5b7e.PNG)

According to its official website: [https://wazuh.com](https://wazuh.com/)

> Wazuh is a free, open source and enterprise-ready security monitoring solution for threat detection, integrity monitoring, incident response and compliance.
Wazuh is used to collect, aggregate, index and analyze security data, helping organizations detect intrusions, threats and behavioral anomalies.


_Wazuh is used to collect, aggregate, index and analyze security data, helping organizations detect intrusions, threats and behavioral anomalies._

It contains the following components:

- **Wazuh server**
- **Elastic Stack**
- **Wazuh agent**

Now let&#39;s explore how to deploy it. For the demonstration i am using a Ubuntu 18.04 VM.

`sudo apt-get update`


`sudo apt-get installcurl apt-transport-https lsb-release gnupg2`

![](https://lh4.googleusercontent.com/rPGSrniewefygNejAp0QdlOS6Zb-cXXZVnjSQa5A3f8SA6IxIlZsFAF-HKvaSXSJs79xZ3S888c2KSctbF38CW4uhH83CZr0Mu_dladGL5ZIG03ajKsNufIlLZICq8iAS8TR0sU)

Install the GPG key:

`wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -`

![](https://lh6.googleusercontent.com/kXCT-lx-YV3WoieP55itv5Q_hPodKNC-sqPsbyW4BJpiIrSfICdP8fmMXqBeC79RFhyylNwOE5pkV4VkFyNHQe-_v6rmDGDpd-TSa6H6yoh7oRoxf1osOZX_QZpcmzS_gheEDCE)

Add the repository

`echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list`

![](https://lh4.googleusercontent.com/X6rA11OoboyiR1qlP8h7edNPR_wN64uMH2gAc6Fs5k9wpToCXf5G4Ej1tbmNgGbMF8i1CctfrzQ7Udrs41M7gIP2rBvwXjo9dJ2p0dX6XKQejWij_28B7PXsz4WJZyqFci8kUDA)

Update the package information:

`sudo apt-get update`

![](https://lh6.googleusercontent.com/Y22Fq1ckWXXVGskuRt9tibDBe_YinQNk4lWIpRbqWV6QrbX-sp5nfHHVmQkwIYJKKoU2kJ3PR1nuI3GHW1xOR5jH_aIEMXdx7g6M45V5Z-kL3LByRqUWRZIDQhIXVt-4QgecKws)

**Installing the Wazuh manager**

![](https://lh4.googleusercontent.com/1QPbDSCiZgDA7RSWS8QMROWCRktHZCPs6OtrAbkp56mxa2trJ4MwSziV5kRqPa3Dzif4ZBMPW2rpVhY-QGUuyXDxRbhuVJinTC0JIaTuLGg2r-1Gz8ook9XnIT0VExm0I53LFHc)

On your terminal, install the Wazuh manager:

`sudo apt-get install wazuh-manager`

![](https://lh4.googleusercontent.com/3CCeEv6kVLqGfCRiltizJ45LfmAF68CQIaDcy6BrlxoqxU_Upg-zvRPvExmBRkWDWenK3Yyc8qytLLNCHhtSOkRPAqdBzz9Ky1s4-iJThoR9nKZKD28j7HHHXx3kbxZ-kI2byNA)

Once the process is completed, you can check the service status with:

`service wazuh-manager status`

![](https://lh4.googleusercontent.com/wzWF1yOJCYNEpSq4Ae98VTeWPrCFfNUHVwjNFN0ZY75P8BlJp1_x7PN6mqtb60vRd4Dhrgy3hGQsjXktB6zgpFCcaJ9bq3j9vai4FVbzfUtSj0lu49KIk84bLKnb4FHYzTmYZ4k)

Installing the Wazuh API:

NodeJS \&gt;= 4.6.1 is required in order to run the Wazuh API.

`sudo curl -sL https://deb.nodesource.com/setup_8.x | sudo  bash -`

![](img/nodejs1.png)

and then, install NodeJS:

`sudo apt-get install nodejs`

![](img/node2.png)

Install the Wazuh API:

`sudo apt-get install wazuh-api`

![](https://lh4.googleusercontent.com/iWhNmLfK8v-CFon8yNYEYO8yFaApeagGEv--E8lBWwg1FDNpODASeTUdFDCpOH52kZfOLeQ7YfchP5F52xWKsHX3B8xdfu1cGZrPqx0ePan9AhZsFbfVB63mJ6byvVPboEHilHA)

Once the process is complete, you can check the service status with:

`sudo service wazuh-api status`

![](https://lh3.googleusercontent.com/PomeXscKz-g0vX9udvsWkg-ChqW0BgrHFAKbqYL2GRoYhIzbiExfGl4VArD4dSr0bFfDir7Z-DOMTw1p9xt3uphYnARZEeXKeJsiRuw5hJbk8xwLnQX4HU93dd8WUaRV4NWuK7w)

**Installing Filebeat**

`apt-get install filebeat=7.4.2`

![](https://lh3.googleusercontent.com/bxByNNLHDEbiUahWid046QzylcB3wwte4degfhLesH-cTdXNCOYN8Aq5ripN_eNx1o1aIaFQaY0RQAjhNqephmR8xGTm6RuDZ9EzT65KKRsviQBlPVH8vfta4Npho0JiJM6T5DE)

This is pre-configuration to forward Wazuh alerts to Elasticsearch

`curl -so /etc/filebeat/filebeat.yml https://raw.githubusercontent.com/wazuh/wazuh/v3.11.4/extensions/filebeat/7.x/filebeat.yml`

Download the alerts template for Elasticsearch

`curl -so /etc/filebeat/wazuh-template.json https://raw.githubusercontent.com/wazuh/wazuh/v3.11.4/extensions/elasticsearch/7.x/wazuh-template.json`

Download the Wazuh module for Filebeat:

`curl -s https://packages.wazuh.com/3.x/filebeat/wazuh-filebeat-0.1.tar.gz | sudo tar -xvz -C /usr/share/filebeat/module`

![](https://lh4.googleusercontent.com/UD5gpOzNVzhZG-FjjdwOu9G_P64Hqqrwq8TC9dKGiUDbNOnNVgbnmhctU0pDdsASyFmm_WJtYOCCIgani8mv0jdm2oQDN-bwbpGzlSdbriIfnlaUlTgOn-78nsRdokC7o3I2LnU)

`sudo vi /etc/filebeat/filebeat.yml`

![](img/filebconf.png)

Enable and start the Filebeat service:

`sudo update-rc.d filebeat defaults 95 10`

`sudo service filebeat start`

## Installing Elastic Stack

![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f4/Elasticsearch_logo.svg/1200px-Elasticsearch_logo.svg.png)

Elasticsearch is a powerful open source distributed, RESTful, JSON-based search engine.You can see it as a search server.It is a NoSQL database.To install elasticsearch we need to make sure that we are already installed Java.

`sudo apt-get install elasticsearch=7.4.2`

` sudo vi /etc/elasticsearch/elasticsearch.yml`


    node.name: node-1
    network.host: ["0.0.0.0"]
    http.port: 9200
    discovery.seed_hosts: []
    cluster.initial_master_nodes: ["node-1"]

`sudo update-rc.d elasticsearch defaults 95 10`

` sudo service elasticsearch start`

![](https://lh5.googleusercontent.com/tlBDNOKL8EndSBNdx0ayyUyX0eu4sL_pPADaKZfRcSvt5AIRfoHO-5RY5chAHxTaQ6u83VoHPvGoF9QCOc6zd4Vm6FSIHLUwuH00uLV-IlA5O-JuO7YJ_GZCCdgKhxqwO76yAE8)

Once Elasticsearch is up and running, it is recommended to load the Filebeat template. Run the following command where Filebeat was installed:

`sudo filebeat setup --index-management -E setup.template.json.enabled=false`

![](img/ilebeatindex.png)

## Installing Kibana

![](https://i.pinimg.com/originals/b3/90/4f/b3904fc82bcbd62f10c225a853405df3.png)

Kibana is a Web interface for searching and visualizing logs. It is a data-log dashboard. It contains pie charts, bars, heat maps, bubble charts and scatter plots. It is an amazing solution to visualize your data and detect any unusual patterns

`apt-get install kibana=7.4.2`

![](https://lh5.googleusercontent.com/m9IWpob3hPgugAgCCpmOkEYwuMrOpjpuE0Z_hrojc1JB9Tmdp8mHXMY046_KMqMTCZ2cAllrX9EAE0ZHL6QLIjcAJ_sQQBBUdVMOhyZDGcQKl2YOa5CNLO63dUVC0pJo5Pgwp7A)

Install the Wazuh app plugin for Kibana

`sudo -u kibana bin/kibana-plugin install https://packages.wazuh.com/wazuhapp/wazuhapp-3.11.4_7.6.1.zip`

`sudo vi /etc/kibana/kibana.yml`


    server.port: 5601
    server.host: 0.0.0.0
    elasticsearch.hosts: ["http://localhost:9200"]

`sudo update-rc.d kibana defaults 95 10`

` service kibana start`

**Transform  data with Logstash (Optional)**

![](https://i.pinimg.com/originals/8b/29/ff/8b29ff73ef1f198e3598f1214901f323.png)

Logstash is an open source to collect,parse and transform logs.

`sudo apt-get install logstash=1:7.4.2-1`

` sudo systemctl daemon-reload`

` sudo systemctl enable logstash`

![](img/installlogstash.png)

Download the Wazuh configuration file for Logstash


 sudo systemctl restart logstash

 sudo vi /etc/filebeat/filebeat.yml\&lt;/a

Configure the Filebeat instance, change the events destination from Elasticsearch instance to the Logstash instance.

Disable Elasticsearch Output:


Add:

output.logstash.hosts: [&quot;localhost:5000&quot;]

sudo systemctl restart filebeat

Check if Logstash is reachable from Filebeat.

sudo filebeat test output

![](img/filebeattest.png)

Replace the default credentials with your desired username where myUsername is shown below to protect your Wazuh API

![](img/apicridentials.png)

More information: [https://documentation.wazuh.com/3.3/installation-guide/installing-elastic-stack/connect\_wazuh\_app.html](https://documentation.wazuh.com/3.3/installation-guide/installing-elastic-stack/connect_wazuh_app.html)

Open a web browser and go to the Elastic Stack server&#39;s IP address on port 5601 (default Kibana port). Then, from the left menu, go to the Wazuh App.

Click on &quot;Add new API&quot; and fill the API fields. If everything goes fine, you will get this main Wazuh dashboard.

![](img/dashboard.png)

To add new agent just select the OS, curl the package and install it:


![](img/wazagent.png)


