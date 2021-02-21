**Filebeat Logstash to Azure Sentinel**

In this new post we are going to explore how to send events/logs to Azure Sentinel using Filebeat and Logstash.

![](https://lh5.googleusercontent.com/83efHTi2pNWppBntTzwv6Gd2TFF10fJ4LRUqwCOhUutfIqn3ivisi1F8k23MZtRHLIjAc9ZBrePVdmsHz_Ga0q_nRGwgPJoNk9oCJ4xPkezGudElQpmvA2DcGuXsNFR_FBpa5Uol)

**How to install and Configure Filebeat:**

![](https://lh4.googleusercontent.com/SKOuLn8m0FPjp4L7J0tFEZQH_UZmftu8dkIDw9gDVdcFfirJYRbie5DK2WnI0rVucu7jgXodHqj9_P2hqVASZYFPwfq65vzJOrgtTDKRfTHHO6FLZXP3t4Na3ghNhBtN6I51dZZO)

Filebeat can be downloaded from here: [https://www.elastic.co/downloads/beats/filebeat](https://www.elastic.co/downloads/beats/filebeat)

To install filebeat run the following commands (on Ubuntu 18 in my case)


```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```
```
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list 
```
```
sudo apt update
```
```
sudo apt install filebeat
```
![](https://lh4.googleusercontent.com/EBbjqsoZnqV6DeSkJU-gDVBczVGjgIKzU7z_T7XpRxx9lf5zpt36TB1SK_-BKTYAqauhzC5hNxmMBRlTOjij5Wdza5Xl4lli7kjkWjuk1lR5wfiYBalNtWxjbrpPvRfTvvIAkoFr)

Filebeat comes with some available log modules such as the following modules

![](https://lh4.googleusercontent.com/0ovL37CkY1HdBG8soBt4T8YaYKVL3BedlyCWiZAghXLKNBPbPxSaKPalDsEXOrJkJO8uolZjtiYl4qT5lA38Uz9R4F3PKzfGIuwV-P7dvURqcNMciDmu9iR8Awh1jxdLbhPvSihx)

For example, let's enable the system module: 

```
sudo filebeat modules enable system
```
Edit the config file:
```
sudo vi /etc/filebeat/filebeat.yml
```

![](https://lh6.googleusercontent.com/kLTArPTTuYqQZFuiEHKascgwoH-6TGVz1aTbVIfk7ElNwYFlSDLI0he0pz-aWAp22H8365PxleE79oIn2DYIWd5njngBhBBFD9dqF3PL9OvPwo3fUFWdkIgdXfdB8a4pVulERBIg)

Comment Elasticsearch Output section and uncomment Logstash output:

![](https://lh6.googleusercontent.com/RM6AuD8UFJ4szuyKQDWheyA_E_vf24yKVi9xRWdWvgiHjcxoZYHOINAipsR0lDfWpV8UE-UXi-09axYT5X4bNRo_3k-3cPn6LZPBiN0JhsLZ38zgVYn7WwQRqi11e8vvhtN8CfYL)

Start Filebeat
```
sudo service filebeat start
```
To check its status type:
```
sudo service filebeat status
```
**How to install and Configure Logstash**

**Logstash**  is a free and open server-side data processing pipeline that ingests data from a multitude of sources, transforms it, and then sends it to your favorite &quot;stash.&quot; (Source: Elastic.io)

![](https://lh4.googleusercontent.com/bRBGmdJK9HURM2ZVsBnhcdzOcsdCGIR9ty-zVq4_3Tj5DDjk8cL3wgXAVVPZwEohR_HGc8D9QCZ2QNsYgPTTlQsGmJAlNzQKjvXtWyiMKOd2VXrwZqacZiGx02nUuE2H81y-sWvz)

Logstash can be downloaded from here: [https://www.elastic.co/downloads/logstash](https://www.elastic.co/downloads/logstash)
```
sudo apt install -y openjdk-8-jdk
```
```
sudo apt-get install logstash
```
Enter /etc/logstash/conf.d/
```
cd /etc/logstash/conf.d/
```
Create a new config file:
```
sudo vi Azure-Sentinel.conf
```
add the folllowing content
```
input {
      beats {
          port => "5044"
      }
  }
  filter {
  }
  output {
      microsoft-logstash-output-azure-loganalytics {
        workspace_id => "<your workspace id>"
        workspace_key => "<your workspace key>"
        custom_log_table_name => "tableName"
      }
  }
```

More configurations can be found here: [https://docs.microsoft.com/en-us/azure/sentinel/connect-logstash](https://docs.microsoft.com/en-us/azure/sentinel/connect-logstash)

Start logstash
```
sudo service logstash start
```
Now you can query events by selecting the table name
