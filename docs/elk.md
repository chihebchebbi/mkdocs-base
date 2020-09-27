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

![](https://lh3.googleusercontent.com/k-upOTt8JOwxY7G6p7LfDlkGtrC9Pj1t8pAPQmEtxEm8vYbxQ7JhW7ieOEmYlm-gANX6YMfVgVifF2NUPwqTl2dSCUKmP8gAoxotVMkmWDycy8eRGTRYGuCRi2LEbp1G7Wm1XBQ)

Install Java JDK 8 (and _apt-transport-https_ if you are using Debian)

`sudo apt install -y openjdk-8-jdk`

![](https://lh5.googleusercontent.com/B2UxXW2O5uXCAP3bWwjLCDvA3GxVxsu-OU1KieFWOrapmnMY5BM4_diLZXSs-gTXS-IVCglNXQtNJj7w8j9KF9aDQUGNKay1KATMQxaVA4_EHF8Fnt9GiwrlKCxvTNBDs-zvl0Y)

Check the Java version with:

`java -version`

![](RackMultipart20200926-4-122n7kb_html_29ea21525978abbe.png)

Now let&#39;s install Elasticsearch:

![](https://lh4.googleusercontent.com/civNjJFKfx-ggDY02MITB82Z0p58QpaK_bVBRaQUwtIwnRwKkIznUniI8AUfIN9bcLKiTGpzFLcI5WZP03jI_JNWwh3cdHz17u00SPsXffUQrS6to7hwAnzjxcZhPtCTz0bntdg)

`wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -`

`echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list`

`sudo apt update`

`sudo apt install elasticsearch`


![](https://lh3.googleusercontent.com/bxruaWQ39xyEt7K5PqoNRaly9H1RlwuAzQRvtaEqyv7wo7fcYKzeqpSlP-EKsWhQ6sYlo7c0jiNSy46WE3pRntPylaMP25FdmljqWm8wtpsWIqOFRK9rik0pAkY28xHjSPa-vvE)

After installing elasticsearch you need to configure it by modifying  **/etc/elasticsearch/elasticsearch.yml ** file

`sudo vi  /etc/elasticsearch/elasticsearch.yml`

![](https://lh3.googleusercontent.com/5noXChiXI98UOvV7qpId532ncXLSKORk8O69ia9JUV_JPx-DaCkQif_LaDrPBm961FY4m1Pmu7N3fu8TWYQJ17T7I7iSjvEpgbGKouxAL7udCgD1MJbmo-_F-cEv04faE0qRax8)

Un-comment  **network.host**  and  **http.port**  and assign values to them. Don&#39;t use &quot;0.0.0.0&quot; in your production servers. I am using it just for a demonstration.

save the file.

To start Elasticsearch on boot up type:

`sudo update-rc.d elasticsearch defaults 95 10`

Start elasticsearch service:

`sudo service elasticsearch start`

Check the installation:

`curl -X GET "YOU_IP:9200"`

![](https://lh6.googleusercontent.com/PQcmB_fWG991yyG4q1ZaJgQe_jhoRgIsRVhHtq-CuKY6MPW_AhNqXvhGB-VesY3lcLgofCY9PVMSb96zMqe0yzltpq677yw638w5MhNpwTckFhTj2IMboQwbzetQWt6BReQBKT4)

Now let&#39;s install Kibana:

![](https://lh5.googleusercontent.com/v-VhNBRNlulkZ2LegsUi-nsJLU6aOC87LP8JCBmlZojCaCTh_oypIb8zsSWwTuQ5uDQoH-NINJs3kveWVMR0K9mtjzJLyahbJ8ec6hoxIVHWiZOTCyy_JgmpJSstQEZE9uHVcVU)

`sudo apt install -y kibana`

![](https://lh4.googleusercontent.com/7oiS00elufF2XPRAokvkcRHChbubp-s5sDDVC9fhGh5bdJ7baGXaPrGyM8jrJ3bCKDw-b6GmaNAW66C3QEPAJg0fmymVgV98ph5XMWfT8Xxyi-DoozbpNfduu4T3iV6ruiEYrFU)

And like what we did with elasticsearch we need to configure it too:

`sudo vi /etc/kibana/kibana.yml`

![](https://lh6.googleusercontent.com/Kd2deBruvxeXQSHyTuCbPULnbkqSmppzu_34N3cJroHzfdGNjwOlh8EMe46Y0B4gmDDqNUzDm_dw0D2F1Bcik43ZGjHkp8k3j7qT4xZXKKk1p4JHaSSlfO-EUDNHFsheDvgRQ38)

Un-comment and modify the following values:

    server.port: 5601
    server.host: "YOUR-IP-HERE"
    elasticsearch.url: "http://YOUR-IP-HERE:9200"

Save the file, and perform what we did previously

`sudo update-rc.d kibana defaults 95 10`

 and run it:

`sudo service kibana start`

Now go to [**https://YOUR-IP-HERE:5601**](https://YOUR-IP-HERE:5601/)

Voila, you can start exploring the dashboard of some pre-installed Sample Log data: ![](https://lh5.googleusercontent.com/Jns1eR4qb6jjDIjE9CAoGSdD7vieqFJaZmn44fFYmZ6yDkB10uXBAVuvyFimN709C-KEQ9I-EVynfJA7FZO0eXmxGz8H3uWRHeJCH3cZom5w5us95neYADMEvMZzMpo1leCg-zo)

![](https://lh3.googleusercontent.com/XB6rTU1BwkkAgMBBZQkA5Dbt0BNRPc6f1V1lcwpD3PsBTudOISLij5-0a6v6KMaRBaySmZ_w5D8a9IwvFpSxyvR_ZzT6oQlw-KFQGi5MAicVeZevyNZKjHrnKU4tFLGlO_D2Xv4)

Install  **logstash**  to collect, parse and transform logs if needed:

![](https://lh5.googleusercontent.com/VBgELIP6OjcfkIayXw-Lo7JG5EfrXnHOcSYnPmLLfu1UtLp4cY_fW2LeOZmM7FRZiBwXufciQkt25iGI4K5tu2WLOQHt1WNSvJ4A-iLfN17c-PJQ1wuOy4xjI6v1y73M--8hiuE)

`sudo apt install -y logstash`

![](https://lh3.googleusercontent.com/3T9QEBc6gJQFez-72ixFaFC3uGwX6ziMdcjberAPrciMaHSWqIpeNmA6kT7i38tObWWAN2TYA7iI1Q2hhJzGejSR1UJnsLhbRvt7FKQUQgf0Xh1XOSPK4GXIRORW4q1OiWkN810)

But wait how can we use our own data?

It is a good question, we can receive data from a host using what we call &quot;Beats&quot;. You can find the full list here:

As a demonstration i am going to use &quot;[Metricbeat](https://www.elastic.co/products/beats/metricbeat)


`sudo apt-get install metricbeat`

![](https://lh6.googleusercontent.com/K01V0LfZBOHlfnsrrEodDtvD509i57jTQ5JZk_IQ6ibsas6yqaCKAoWAnTHFngwt5w2jKs11oDla-U819-kmUguWDENgCBuzzJm1t1CIukg9cGZwL7jX9lQjpx-oiMRgNdyr9UU)

Configure the beat by typing

`sudo vi /etc/metricbeat/metricbeat.yml`

To start metricbeat on boot up type as usual

`sudo update-rc.d metricbeat defaults 95 10`

Start the beat:

`sudo service metricbeat start`

Now go to the main dashboard and create a new index:

If everything went well you will see your beat:

![](https://lh3.googleusercontent.com/k1xJ5Q-wgKb5GWmZGXy0J6HMszgKDJqFItHzFvBZRxproMfdJ3E8nrwNtGNROw2WcDh1MHcDKAA_SNPvKY6kHufT5jKVXsqn8UMeHEI6U5g5jqgLpzATKgKJEauqOT8Z9zwmCFI)

Select the time filter by selecting @timestamp:

![](https://lh3.googleusercontent.com/zoEHYQcixMbEDktdQTJaHALZFUQ1LTDyxvYlWdbqTbW6QTStG76moe0bMq-cZrhpv2zkJRlpWciYnEy_DIzkNj2K43erDUBq5GDCNsQx7oLtHimS7S75-QwM6lBmPFxb2PHa96Q)

Then, you can visualize any data you want from that beat.

By now we deployed the most important parts. Let&#39;s learn how to deploy the ELK SIEM:

Go to the sidebar and you will find SIEM option:

![](https://lh3.googleusercontent.com/GqUKMqmmwmQp6vPoos2uzU0cuknWV5ZLXjmvKoweRYi2HYKHKAqsFnmU33AhEV_0IoxOrEscQp5GbKGGDFHUVItdGst_HPRMPycAiiTfOXsLmzHsJYulazL_y_RTldsGvs7Q78A)

It will take you to the main SIEM page:

![](https://lh6.googleusercontent.com/XzMdJDVXnlNHYu-sYKkLy5RhxqwmAi6d73fKJu5xf1Sms5oKttItYbQSEb3Io45TBAObv3ZPbjEDlJGDfGhdDWmUj9HcxtdGuL9SJYg80dnmN8KMKZU9SBBRHdhb3SdgY780zSs)

But now we need data to run the SIEM. In order to do that we need to install other beats from sources like the following:

![](https://lh5.googleusercontent.com/onayh7HT6Nn9zDc-JSzXWRJ08wPjQdy4vPx82qPE31t0bCdC4T89RmxX1ocxS-UVN3IT5VZQIXtUOAzyxoKYK-Fft1m1vfmgoRwEoM4TSIxpB1PoERlcx6S0QbeqCW52n9Gjyps)

For the demonstration i am going to use the &quot; **Auditbeat**&quot;:

`sudo apt-get install auditbeat`

Configure it by:

`sudo vi /etc/auditbeat/auditbeat.yml`

Check the setup:

`sudo auditbeat setup`

![](https://lh3.googleusercontent.com/Wv3x6cQJ8tF0qA2TrVxm_dzbPcyF4ddXwRCi2Nc_ZlgY8rq-nSxKnlLY-xWlpev2HXLt8VTT5Jy7NUyvhq0s3hgYpfnvX_yzTxE1hDm-eQAu5dtL74Z8Q2OoSq31uAuyLmzPcmU)

Run the beat:

`sudo service auditbeat start`

If you did everything correctly you will see this on the SIEM Dashboard:

![](https://lh3.googleusercontent.com/_uXL_LXpY-ooqreP_qalxpx7V5YLSOhLUZa829ph5cqtdsB-Z6df2vcrw0JJlStLJ53DBxXcd0C5jr5nsmRIZzO-CgETvD1h6X7AMRNL11PeDsW_qTfTY8sH6MDzlNTaD_QLQfk)

Congratulations! Now you can see the dashboard of your SIEM.

![](https://lh4.googleusercontent.com/ZCTe7JJtTS984bRFyqaR7IfTBS2AOGjyAubcWLzsvBikE4NBrilp0a9nh645mBvt06qFEyHZfj55dEaG_86-2FqFOZ3QFQ-GFCo4dilwL0gpHvwcL-ZKjKNQaXlSRQ1-I0nN4wE)

Check the hosts:

![](https://lh3.googleusercontent.com/xfkQR4dqJih3m4kjV5losgf8XrjSpdSHzUExY6upC6gSg8KJVdvn4Yzk3Spi_61OQ57K2sy846q0mj2n30UN07G1xJjnnMpY9Xz95NGZJR84m3a9x2TswNiZeDr0M-xquPj4JcE)

![](https://lh3.googleusercontent.com/LylO9HDkVGgRC_b-ogp5qb0GgdGNzDTn0r1JsOaqGGQlzhiA78qQaNx5dk0s68VXp0goxiS0U1IPcBwSQTwFt-Hlszty2sZZcB-0-6dBTyzmHoZdtUslgy_m4iZR4dzfdbo2qUU)

Check the Network Dashboard:

![](https://lh6.googleusercontent.com/PvI4sTvSPV1TiPANlLykwXDjYlPKDoOCOSk7tNpmKd9VVhJRDvFxKqWcMkRXS98vAQjdwuL3BkOKzT2dvv03m2Z8HlIyv9xL1K965SV9aPb4xEmLRGWd-vINPZy20ivZaZgq5co)

A system Overviews:

![](https://lh5.googleusercontent.com/ba1MI1ylHnnX1MP16_sMWPuyBPufQmYDDBThq91yACZQSVYXMMNa0TbPkhZkh3k6vnYjMMVzjotl_q7FGoQUP_Z2GUrMbIxzdgLeBbksWHXQU-iyBrU39nzfyPy2jGdStBzmGVU)

![](https://lh4.googleusercontent.com/T1XCEuu5frtM6LReozWUjkuqnipiv999f3rQ43JipYirz8hvedL_bFqd_MEi4cw0I_rnoK2klOz6JG3AJty5DpRHTzUxsBrRv2yHdBSS7IZ0GzPs75CZ9WoeWYNlg4ndgvGZFTY)

Voila, you learned how to build an ELK SIEM.



