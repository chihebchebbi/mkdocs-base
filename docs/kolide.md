#  Incident Response and Threat hunting with OSQuery and Kolide Fleet 


In this guide, we are going to explore some powerful tools to help you enhance your incident response and threat hunting assessments. These tools are OSQuery and Kolide Fleet.

![](https://github.com/kolide/fleet/raw/master/assets/images/dashboard-screenshot.png)Image source: [Kolide Fleet dashboard](https://github.com/kolide/fleet/raw/master/assets/images/dashboard-screenshot.png)

Let&#39;s start exploring the first tool OSQuery

##  OSQuery Overview 

According to its official Github [repository](https://github.com/osquery/osquery):

![](https://engineering.fb.com/wp-content/uploads/2014/10/1_XC-k2QigREIwZnBpFZ4StA@2x.png)

> _Osquery is a __ __ SQL __ __ powered __ __ operating system __ __ instrumentation, __ __ monitoring __, and__   __analytics__   __framework. It is Available for__   __Linux__ , __ __ macOS __,__   __Windows,__  __and FreeBSD._

Its official website is [https://osquery.io](https://osquery.io/)

![](https://lh5.googleusercontent.com/uFRLKcjjSHWxoQiouzoEoImwYsnB5FmLOQ0PxnHNNlsmb2h5FD9VRSH76GafzT4P0o5ZRykSRdqwJgAtERiPXOaMFBAZ5Qkr7TpgfnDeuK3OufhXCdVfst0ECOqECEp7C-RB4xo)

To download OSQuery visit: [https://osquery.io/downloads/official/4.3.0](https://osquery.io/downloads/official/4.3.0)

![](img/downloadpage.png)

For the demonstration, we are going to use a Ubuntu 18.04 TLS server machine. To install it on our Ubuntu server type the following commands:

`export OSQUERY\_KEY=1484120AC4E9F8A1A577AEEE97A80C63C9D8B80B`

`sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys $OSQUERY\_KEY`

![](https://lh5.googleusercontent.com/5JPbLZvAcj_XdQHO-oWx8MpOi_e7ycjYqz_8IK3k32L1ZxFeOjDlmXXesAmpWQG1_CuwTcN6zUQIb6KjZsa5UWBMwriJgATfAOWy0wHVHvoBVvWZX218KRq_YgQ8m61x2zSQdH0)

sudo add-apt-repository &#39;deb [arch=amd64] [https://pkg.osquery.io/deb](https://pkg.osquery.io/deb) deb main&#39;

![](https://lh5.googleusercontent.com/zHiMKUT8-0C3WkgpX3aNfZMfo9VMb5DH668Zq71SefYwVnYgSXRqth1ZL8PdwHwv5ntRxlZvPKBX-njd70gz742WY5lK7AdCcEGbYtbVWDH7cY6ZLLtRtNEt_KjatKNUacVHw_g)

`sudo apt-get update`

![](https://lh4.googleusercontent.com/lwhKzdNIcSCSa58mvO6CUS2TMdgSmRN2DhiO_m2n4fhhX9zG1M4VvX84e_kQPYv1ivSu73C1RdoV6RnlDueicuvrRGlifHzA9CJGGzRgIO-xSn2a2eMI9aGy6I1R0PwPx0N7s8c)

`sudo apt-get install osquery`

![](img/installosquery.png)

OSQuery delivers these modes:

- **Osqueryi: ** Interactive shell
- **Osqueryd: ** Deamon

To start using OSQuery simply type:

`osqueryi`

To explore the available commands type  **.help**

![](img/help.png)

To explore the available tables type

`.tables`

![](img/tables.png)

To explore the schema of a specific table type

`.schema \&lt;TABLE\_HERE\&gt;`

![](img/schema.png)

For example if you want to get the users type:

`select \* from users ;`

![](img/users.png)

To select loggedin users type:

`select \* from logged\_in\_users ;`

![](img/loggedin.png)

The official website contains the list of all the available tables and its schemes. For example this is the scheme of  **Kernel\_info table**

![](https://lh3.googleusercontent.com/147dE-axobVAkwPj9OkZG2M2V0c7Rjv_i5krN-6pdr89Rtl4nvrEHVcLzxaC5cv-CdZX2h8sUkTHorI8VAigTNUdFq4v3L757UTol1wezjLJZKHTmewMtB5mhMeOkX5xWf_wP9U)

For example to select the version of the kernel type:

`select version from Kernel\_info`

![](https://lh5.googleusercontent.com/OSOVd2rvHHWWemCsOEO2g_UZbqS1F1Xr1vvDpPmX0-eBJOEQNjGWBhH7udxUGMYtnBCC4Q2OstxgEhhei3eisVmmJkvzAzLG-ZLe_jgBfnmCn9uck0zelnO4FEZA0k6qD1s5uEU)

Let&#39;s suppose that you want to automate a specific query (selecting users) every 300 seconds. Edit the  **/etc/osquery/osquery.conf  ** file and add your rules

&quot;schedule&quot;: {
 &quot;Users&quot;: {
 &quot;query&quot;: &quot;SELECT \* FROM users;&quot;,
 &quot;interval&quot;: 300
 }
 },

A collection of queries is called a ** Pack**. OSQuery provides many hekpful packs that you can use in your assessments here: [https://github.com/osquery/osquery/tree/master/packs](https://github.com/osquery/osquery/tree/master/packs)

![](img/packs.png)

This is a query from [https://github.com/osquery/osquery/blob/master/packs/incident-response.conf](https://github.com/osquery/osquery/blob/master/packs/incident-response.conf)  that retreive all the startup items in MacOS hosts:

![](img/packexample.png)

But now, what to do if we want to deploy OSQuery in large scale environments and we want to manage them all easily. In this situation we need another powerful platform called &quot;Kolide Fleet&quot;

##  Kolide Fleet (OSQuery Management)

According to its official [Github repository](https://github.com/kolide/fleet):

> _Fleet is the most widely used __ __ open-source __ __ osquery Fleet manager. Deploying osquery with Fleet enables live queries, and effective __ __ management __ __ of osquery infrastructure._

![](https://miro.medium.com/max/1400/1*t17v4ZaUn-4Nz7tmAJWElQ@2x.png)Image source: [Kolide fleet ](https://miro.medium.com/max/1400/1*t17v4ZaUn-4Nz7tmAJWElQ@2x.png)

To install it use the following commands:

wget [https://github.com/kolide/fleet/releases/latest/download/fleet.zip](https://github.com/kolide/fleet/releases/latest/download/fleet.zip)

![](https://lh6.googleusercontent.com/EHlTQG_k8pkDnxfsBskiq18F4W5ruS_YQkeYygyfe1mWeEa5KagUiWvZmBHF2Oii6XzkIDk1u9RNSK3zZ1JbKpaXOx-JOpU9o2uz7YhKhmJFBVdohQVESw1t_6k6Ydw90KYs5Bo)

`sudo apt-get install unzip`

Unzip the file:

`sudo unzip fleet.zip`

![](https://lh3.googleusercontent.com/IwBRKXA7F85nmashtfiV6CK5j00AcZVXLCwXPLe1ZIiY3VPvDn8OQvoU3Jyc75sQ_mtbaceYfagv2yFsgDLwvzpcYwOx5ZDT5QO1aiqagu6H5qWXQul-F7iqU140I0vSz1B4Qv0)

Enter the linux folder:

![](img/linux.png)

Copy the binaries in /usr/bin

sudo cp \* /usr/bin/

Install this required program:

`sudo apt install software-properties-common`

  ![](img/common.png)

`sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xF1656F24C74CD1D8`

add-apt-repository &#39;deb [arch=amd64,arm64,ppc64el] [http://sfo1.mirrors.digitalocean.com/mariadb/repo/10.4/ubuntu](http://sfo1.mirrors.digitalocean.com/mariadb/repo/10.4/ubuntu) bionic main&#39;

![](https://lh3.googleusercontent.com/SoyNCaMipr02T1MgvFKHJ1_-Un5C2lONbX-FbZhJgIbuU5UDeZMfjPjVJ5M3SBTd3KEUpAiHL_8LC-K623CocFTMOREXQDTaeOO-7uVR9Ku5tPcjo2P3-aPcOzVt3uUPT3P9jk4)

`sudo apt-get update`

![](https://lh3.googleusercontent.com/HK-3Jxo4YrxT4pJeJ4zzWjvHEUe3ZdfVr9RgzrGyOxG7BokFQwoBSeLT9fIMQq453kJEN1I6voU0b9pG9Yxxy66Pie-XQTxgjTVurep7vZZzVv01nLQS3INyvrPQILidR7FcQyc)

Install Maria database server and its client:

`sudo apt install mariadb-server mariadb-client`

![](img/mariaclient.png)

Check its status:

`sudo systemctl status mariadb`

![](img/mariastatus.png)

Enable Mariadb service:

`sudo systemctl is-enabled mariadb`

![](https://lh3.googleusercontent.com/v93JRktG-bC_XZaleZkKAyvDAsI56ryZtSjFNWoC5Ac50e4lGUoJ2aYMjpHuwWnSAMVCQMXb3gjcGvDqrqmkqOSiHD3dAChQDTz-mqNuMvsGyaY1S5wca0tqGk62JuNPQ8MgzFQ)

Enter mysql and type the following commands:

`sudo mysql -u root -p`

![](img/mysql.png)

create database kolide;

grant all on kolide.\* to kolideuser@localhost identified by &#39;Passw0rd!&#39;;

![](https://lh3.googleusercontent.com/MxO3odbh6eRGljfS1ZQArabqwgNtGH6Sb6JKjJBgbSKDnIOXgR2Hh3C9qa5qCZOSEanzqSpdH8qHeCPhdYl8847Fwd259LYvhlsJSSsIlTiIvPj7UQ6_Y-VN-RgeETiCmwcxjuE)

`flush privileges;`

`exit`

Install Redis:

`sudo apt install redis`

![](img/redis.png)

Prepare fleet:

fleet prepare db --mysql\_address=127.0.0.1:3306 --mysql\_database=kolide --mysql\_username=kolideuser --mysql\_password=Passw0rd!

fleet serve --mysql\_address=127.0.0.1:3306 \

 --mysql\_database=kolide --mysql\_username=kolideuser --mysql\_password=Passw0rd! \

 --server\_cert=/etc/ssl/certs/kolide.cert --server\_key=/etc/ssl/private/kolide.key \

 --logging\_json

![](https://lh5.googleusercontent.com/8xH5mWapu5b3sI2F5j2cKad-MkW8lwvXFmJXOB59nh0poTm2ARFUybjeVJfdyT0VIoMgsh1Yqqjy4M0Xlbs5wHR0W4sILKlZSIuMGJnfjjZC5uBN8k7SCifJTZxe7Dxy_c4nApo)

sudo fleet serve --mysql\_address=127.0.0.1:3306 \

 --mysql\_database=kolide --mysql\_username=kolideuser --mysql\_password=Passw0rd! \

 --server\_cert=/etc/ssl/certs/kolide.cert --server\_key=/etc/ssl/private/kolide.key \

 --logging\_json --auth\_jwt\_key=9yKI2MeThUSLtsYiCS7etUSJZD1lgHLr

Start fleet:

![](https://lh3.googleusercontent.com/JG2DVPfLEpRl0tkASKI-0F04mLlQu2YKfaeh-SEka1jQ5cKxMNTWdoVJJ4siABL-PWCd5_yPLFpJwkxhKPGGrOBUkZRSB1mVkLLix-uopJBuPTV5yOMkH7Q6-f017u3-E0za8oc)

Go to https://\&lt;SERVER\_IP\&gt;:8080

Provide your username, password and email

![](https://lh4.googleusercontent.com/io9BtgZDbHfoq996Qs01TJZNGtKKKYlMQDOS0f_fXbTJlSB7rEaKLwfBhPLqkM-85SIiCqZqDb2TlIRsoXHfWi9mWy6XINtyGK5pP9miTC5jqr_qSFIVXcuuSu5xHbBatRDs9Hw)

Add your organization name, the organization domain name/IP  and submit:

![](https://lh6.googleusercontent.com/sgY8-az7BcJ0lzs1taVztBIjJVNVG0_GOg_9ZS3b0wyQNlejgjrG8_J7JrfQjSpmgmOnRG_joaxa5HmSOo6vKOcfikAM8KSTxHxIxcgVy3zJM6yNhrKh7RvdzeweUTSNY868Ngk)

Voila! Kolide fleet is deployed successfully.

![](https://lh3.googleusercontent.com/Svs9SBG8SwUFNrRqYlryS8l703BN-gONe9YXotBq8wGDDDf52VjgUTEmSkrvtnKFRryXe7Wws23VuqKfbokjqb6Vd5eax3KUEXzywJajX6JRK5d4MNdGiBSepXnPBRrQL3WlFJA)

Now let&#39;s add our host. To do so, click on &quot;ADD NEW HOST&quot; and you will get this window. It provides a key called &quot;OSQuery enroll secret&quot; that we are going to use later.

![](https://lh3.googleusercontent.com/QIAN9RMkfqEONL0Pq092kGYA3sgaYqmSJjseS9r6A8WoAu8PzKrqR4364T30cN4QRgrF7PXIcrvEl5NOJy5c6bUKIZfeXtL7FJit6axE5tYKybv3k-05H0fx7Fqq3D7-7IBQ0-M)

To add the host, we need to install the fleet launcher. In our case we are using the same host.

wget [https://github.com/kolide/launcher/releases/download/v0.11.10/launcher\_v0.11.10.zip](https://github.com/kolide/launcher/releases/download/v0.11.10/launcher_v0.11.10.zip)

![](https://lh6.googleusercontent.com/T_t_Z55TYVTQGrbm30jthNNiSLgzxfslC2RFvJOxMisdIPABaeZhfFGwdR4EfXwKFltLhhl4RlfIRi1BwP79_uTKSDWj7MhiWEsze82YddDAWE9ogGOWz81fQl_6gJQEU9WnXOs)

Unzip the file:

'sudo unzip launcher\_v0.11.10.zip'

![](https://lh4.googleusercontent.com/UVvLk5WrC8dVw4zuXhLzQqmBuW5ZntvtPtFBrMu8yP8wZpzRYZTOrcoohSvx4vucCdBeiDae1h6fuwkkaXz13RniiJD4Ezt1JaWBMu3DYZcDjW7zGU9USFzs8XBg2kns0zTgQMI)

Enter the Linux file:

`cd linux`

Start the launcher

./launcher --hostname=127.0.0.1:8080 --root\_directory=$(mktemp -d) --enroll\_secret=\&lt;COPY SECRET KEY HERE\&gt; --insecure

Congratulation! if you refresh the Kolide fleet dashboard you will see the newly added host

![](https://lh6.googleusercontent.com/WTXzaOkaj9YhE8aPoXLFbynmRU1v56RO6u9A7vmQ9YmohjQertSEQ1ItSyt8_S9roD4zZjle83YKYWfS5K5GzvFv20uGTi5Psj5vz2FPvfaBE_vfIBDf4t8wLeFKe6Fn9CkASg4)

To run and add queries go to  **QUERY**  -\&gt;  **New Query**

Type the SQL Query

![](https://lh6.googleusercontent.com/x7zpTF0Uj6LYbdnH3k62gKYI327xFoc7yk-JB-L3haYTuQRJ60DTsWcf6ixZV3RWRJkH9cb9whyqEoI_Vbh2e3fDucDvr3mhRXHr6OVzrVq1WkdpMYusC7LkSsdsBPpBXeXNjtg)

Select the targets/hosts

![](https://lh3.googleusercontent.com/cfyi5ICfqYo8yzL5zeSGHycoXT4BiFJRNAH2BmsrD9QWTKjpnaQpwpvOkdxuGnsdpnaNos3PFP_mcJiqBarjO4ZdkZeNln5ZzXT4rxnhU7hIywp9WgWC6QnV43dh3rgEOfFUWwY)

Click on &quot;Run&quot;. You will get the query outputs below:

![](https://lh3.googleusercontent.com/z67aM2nBNu1alr8hiqC0sfO0xLOwfJ0sPyrFHhiOdiRlL8rykJLPwevbTHbq_oI8vMt9zqGwf1gZTG7sS0WU9MxY3z6OV0vZ79J6d3Q3U9cBx3Zp1nAkF_BH-IEA0XgyRQD6yuE)


## References

1. [https://medium.com/@sroberts/osquery-101-getting-started-78e063c4e2f7](https://medium.com/@sroberts/osquery-101-getting-started-78e063c4e2f7)
2. [https://www.digitalocean.com/community/tutorials/how-to-monitor-your-system-security-with-osquery-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-monitor-your-system-security-with-osquery-on-ubuntu-16-04)

