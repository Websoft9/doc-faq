---
home: false
heroImage: /hero.png
actionText: Documentation →
actionLink: /alldocs.md
footer: MIT Licensed | Copyright © 2019 Websoft9
---

# Most Common Problems

Problems listed below are mainly **technical problems**. For **non-technical problems**, refer to [business faq](/bz-faq.md).

## Is there a Guide for the product?

Yes, we offer online documentations for each image. See [All Docs](https://support.websoft9.com/alldocs.html) for reference.

## What's the username and password for Cloud Server?

**Linux**

* Host Name: Internet IP or Public IP of your Instance
* Connect by: Online SSH on Cloud Console or SFTP/SSH client tools 
* Password: It was set by yourself when created an instance. If you forget the password of Linux, reset it on **Cloud Console**.
* Username: Different Cloud Platform has differences.
   |  Cloud Platform   |  Administrator Username   | Other |
   | --- | --- | --- |
   |  Azure   |  It was set by yourself when created VM.   | [How to enable root access?](https://support.websoft9.com/docs/azure/server-login.html#sample2-enable-the-root-username) |
   |  AWS CentOS   |  centos   | [How to enable root access?](https://support.websoft9.com/docs/aws/server-login.html#sample2-enable-the-root-username) |
   |  AWS AmaonLinux   |  ec2-user   | [How to enable root access?](https://support.websoft9.com/docs/aws/server-login.html#sample2-enable-the-root-username) |
   |  AWS Ubuntu   |  ubuntu   | [How to enable root access?](https://support.websoft9.com/docs/aws/server-login.html#sample2-enable-the-root-username) |
   |  Alibaba Cloud, HUAWEI CLOUD, Tencent Cloud |  root   |


**Windows**

* Host Name: Internet IP or Public IP of your Instance
* Connect by: Remote Desktop Protocol or Online Management on Cloud Console 
* Password: It was set by yourself when created an instance. If you forget the password of Linux, reset it on **Cloud Console**.
* Username: Different Cloud Platform has differences.
   |  Cloud Platform   |  Administrator Username  |
   | --- | --- |
   |  Azure   |  It was set by yourself when created VM   |
   |  AWS, Alibaba Cloud, HUAWEI CLOUD, Tencent Cloud   |  administrator   |

## How to connect/login to Cloud Server?

Refer to this section: [*Instance*](/tech-instance.md).

## Can't connect to the server?

There are two common reasons for this problem:

* Your port of Security Group Rules is not allowed.(Port for Windows server: TCP:3389; port for Linux server: TCP:22)
* The server failed to connect to Internet.

If can't solve the problem on your own, please contact the Customer Service of Cloud Platforms.

## How to upload files by FTP?

FTP is not installed in the system by default, but you can manage files in an **easier** way:

* Windows server: Connect by [Remote Desktop](/tech-instance.md#Connect-windows), then copy and paste files.
* Linux Server: Connect by [SFTP](/tech-instance.html#Connect-linux) and manage files by visualization interface.

For details of the above methods, please refer to this section: [*Instance*](/tech-instance.md)

## How to start initial installation?

After deploy the image to your server, you're required to complete the `initial installation` to begin your follow-up actions.

Generally, there are two entries to start initial installation:

* http://Cloud server Internet IP
* http://Cloud server Internet IP/9panel

If you failed to enter initial interface by both two entries, please check if **TCP:80 of Security Group Rules** of your server is allowed. 

> Notice: For some image, you have to login to your server to initialize by modifying configuration.

## Can't access *http://Cloud server Internet IP?

Possible causes are as follows:

* **TCP:80** of Security Group Rules of your server is not allowed.
* The image you installed doesn't support this type of access.
* The image you installed is not the target one.
* There may be Internet failure of your server.
* There may be some problems of the image.
* Others.

No matter what the cause is, please contact us for [support](https://support.websoft9.com/contact.html) at once if you can't access.

## What's the password for database?

Password for database is stored in a particular file of your server:`/credentials/password.txt`  。

To have the password, [connect to your server](/tech-instance.md#Connect-linux) and run this command:`sudo cat /credentials/password.txt`  

![password](https://libs.websoft9.com/Websoft9/DocsPicture/zh/common/catdbpassword-websoft9.png)

Besides, you can use **[WinSCP](https://winscp.net/)** and other SFTP tool to open the file in which password is stored and get it.

![password](https://libs.websoft9.com/Websoft9/DocsPicture/zh/winscp/winscp-checkpasswordfile-websoft9.png)

## How to manage the database？

Using the deployment solutions we provided, there are three ways for you to manage database:

1. Login to the server and run command line.
2. Use dbForge, Navicat and other local client tools.
3. Use browser version of GUI management tools. (recommended)

Browser version of GUI management tools include: phpMyAdmin, phpPgAdmin, adminMongo and more.  

Entry address:

* phpMyAdmin for MySQL: *http://Cloud Server Internet IP:9090*
* phpPgAdmin for PostgreSQL: *http://Cloud Server Internet IP:9090*
* adminMongo for MongoDB: *http://Cloud Server Internet IP:9091*

> Those are the common entry address, to get the precise address in the applied document.

## Database clients can't have remote connection to database?

For safety, remote connection of database is closed by default. If you need remote connection to database by local clients, at least three conditions are required:

* For settings of database server, **remote connection is allowed**.
* Port for remote connection to database of Security Group Rules of your server is allowed. (Eg: Port 3306 is needed for MySQL)
* Network from local clients to database server runs smoothly.

Refer to our manipulates documents for details:

* [MySQL Remote Connection](http://support.websoft9.com/docs/mysql/solution-remote.html)
* [PostgreSQL Remote Connection](http://support.websoft9.com/docs/postgresql/solution-more.html#)
* [MongoDB Remote Connection](http://support.websoft9.com/docs/mongodb/solution-more.html#)

## How to configure the domain?

There are two steps for domain configuration:

1. Domain name resolution: Operate on domain console.
2. Domain binding: Connect to cloud server and modify the domain item of **vhost configuration file** on cloud server.

Where is the vhost configuration file? It depends on the HTTP server. Generally speaking, there are as follows:

* Apache vhost configuration file: */etc/httpd/conf.d/vhost.conf*
* Nginx vhost configuration file: */etc/nginx/conf.d/default.conf*

## How to back up?

Back up is necessary when using cloud server. If you don't aware the importance of backup or you have no idea about how to back up, please refer to this section: [Backup](//tech-backup.md)

## How to change or redeploy image?

Changing image means reinstalling the system. It happens when users cancel subscription or change the product and more.

Image redeployment is to restore the image to its original state. It happens when conduct test.

Alibaba Cloud, Tencent Cloud and HUAWEI CLOUD support to change image based on the existing server, while Azure and AWS don't support this operation.

If you need to change or redeploy image, please refer to this section:[Instance](/tech-instance.md)  

## How to set HTTPS?

We provide default support to SSL/https for all products. To use HTTPS,users only need to run the following commands:

```
sudo certbot
```

On the process of HTTP configuration, some unexpected problems may occur. To solve problem, please refer to this section: [HTTPS](/tech-https.md).

## How to configure SMTP?

There is a particular section about **SMTP** configuration for your reference: [SMTP](/tech-smtp.html).

## How to configure Security Group?

Using Cloud Server, users can control access by **Security Group Configuration** on the console without paying attention to the firewall of CLoud Server.

The most common operation of Security Group configuration is to enable one port, such as: TCP:80.

Different Cloud Platforms have different operations. To set Security Group, refer to [Instance](/tech-instance.md).

## Where is the root directory of application?

Websoft9 have standardized the directory:

* */data/wwwroot/appname*  the application directory, appname is the product name, e.g. wordpress
* */data/apps* the tools for application, e.g. phpmyadmin

## How to modify the root directory?

When completed the deployment of image, you have a default example directory:`/data/wwwroot/example`   

If you wan to modify its name, path, you just need to modify the **vhost configuration file**:

Following is the sample of Nginx vhost configuration file:

```
server
{
listen 80;
server_name example.yourdomain.com;
index index.html index.htm index.php;
root  /data/wwwroot/example;
error_log /var/log/nginx/example.yourdomain.com-error.log crit;
access_log  /var/log/nginx/example.yourdomain.com-access.log;
...
}
```

> You should known that one Cloud Sever can deploy many websites or applications. The **root directory** is just for one of the websites, it means that one website have one root directory.

## The network is timeout when upgrade on install plugins?

You may have network timeout error when you upgrading or installing plugins for WordPress and ownCloud.

**Common network timeout scenarios**

* Online upgrade
* Install plugins or extensions in Marketplace
* Register account in application
* reCAPTCHA verify 
* Google maps or fonts
* The third resources in your application codes, e.g.  CSS/JS
* Docker pull image
* yum / apt update

**Why this problem?**  

The main reason is that the resource (or service) that needs to be accessed is stored in the foreign server of the application provider, and *application server - application provider server* is subject to regional reasons, and occasional or continuous network failure may occur.

Once the network is unavailable, the services corresponding to the above scenarios are naturally inaccessible, and finally the result of the system timeout can be accepted.

**How to solve it?**

Since the network is blocked, and we can't make any action on the network of the application provider server. Obviously, only by responding to the application or the server network situation where the application is located can we explore a suitable solution:

1. Modify the code in the application to replace the service that is not connected to the network. For example: change the Docker warehouse address.
2. Temporarily modify the application's own network access so that the application can directly connect with the application provider server. For example: install a proxy plug-in in WordPress to temporarily allow WordPress to access the upgrade server abroad.
3. Temporarily change the network of its own server to connect it with the application provider server. For example: install a proxy client in the application server so that the application server can access the foreign upgrade server through the proxy.

The scheme proposed above basically covers all scenarios, but the detailed operation depends on the specific application.

## You need our help desk?

* If you have subscribed image on Cloud Platform, you can get help desk by[Professional support](https://support.websoft9.com/contact.html)
* If you don't have subscribed image on Cloud Platform, please submit issues on [Github repository](https://github.com/websoft9)
