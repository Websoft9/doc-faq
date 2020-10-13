---
home: false
heroImage: /hero.png
actionText: Documentation →
actionLink: /alldocs.md
footer: MIT Licensed | Copyright © 2019 Websoft9
---

# Most Common Problems

Problems listed below are mainly **technical problems**. For **non-technical problems**, please refer to [this section](/bz-faq.md).

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

## 应用源码存放在哪里？

由 Websoft9 提供的应用，规划了统一的存放目录：

* */data/wwwroot/appname*  存放应用本体，appname 即应用名称，例如：wordpress
* */data/apps* 存放应用所需的支持工具，例如 phpmyadmin

## 如何修改网站根目录？

当你部署运行环境镜像后，默认网站目录为：`/data/wwwroot/example`，也就是一个示例目录。  

如果需要修改为其他目录，需要找到对应的**虚拟主机配置文件**，修改其中的网站路径配置项即可。

下面以 Nginx 为例，root 字段即对应的网站目录地址：

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

> 服务器都可以部署多个网站。对其中某一个网站来说，其对应的存放目录才可以称之为**根目录**。

## 升级或安装扩展时网络超时？

在使用 WordPress, ownCloud 等应用时，可能出现在线升级等操作由于网络原因导致失败。  

**常见网络超时场景**

* 在线升级
* 应用市场安装插件
* 在应用提供商的平台上注册账号
* 程序中的 reCAPTCHA 验证
* Google 地图
* 程序代码中第三方资源（CSS/JS等）
* Docker pull 镜像
* yum / apt 升级

**出现这个情况的原因是什么呢？**  

主要是需要访问的资源（或服务）是存放在应用提供商的国外服务器中，而 *应用服务器 -- 应用提供商服务器* 受制于地域原因，可能会出现偶尔或持续网络不通的情况。  

一旦网络不通，那么以上场景所对应的服务自然无法访问，最后只能接受系统超时的结果。  

**如何解决？**

既然是网络不通导致，而我们又无法对应用提供商服务器的网络做出任何动作。显然，只有从应用或应用所在的服务器网络情况做出应对，才能探索合适的解决方案：

1. 修改应用中的代码，将网络不通的服务替换。例如：更换 Docker 仓库地址。
2. 临时修改应用自身的网络访问，让应用可以直接与应用提供商服务器连通。例如：在 WordPress 中安装代理插件，临时让 WordPress 访问国外的升级服务器。
3. 临时改变自身服务器的网络，使之与应用提供商服务器连通。例如：应用服务器中安装代理客户端，使应用服务器可以通过代理去访问国外升级服务器。

以上提出的方案基本包括涵盖全部场景，但详细操作需根据具体的应用而定。

## 网站访问很慢？

网站慢最常见的原因包括如下几个方面：

* 带宽不够
* 服务器满负荷运转
* 图片、视频、CSS/JS等静态资源太多

我们在大量的实践中，发现中国的云用户（国外的云平台用户没有这个问题）普遍存在**带宽不够**的问题。  

为什么会出现这样的问题呢？

一方面是由特殊带宽计费商业模式导致，另外一方面中国地区的用户对带宽的大小是没有概念的，是模糊乃至错误的认知。  

**举例说明：**

如果您拥有**2M**的**包年包月**带宽，打开一个首页大概为4M的网站，大概需要几秒时间？

80%的用户认为应该是在2-3s内打开，实际上呢？

```
1M 带宽 = 128k/s 的下载速度
2M 带宽 = 256k/s 的下载速度
4M 页面的最小下载速度：4000k/256=15.6s
```

这个15.6s还没有考虑服务器的计算、网络延时等时间，所以访问一个带宽只有2M带宽的网站，需要20s也就不足为奇了。

**如何正确选择带宽？**

正确的方式：服务器采用**按量付费的带宽**，带宽的大小设置为最大（有些云平台高达 300M/s）

> 国外的主流云厂商，没有包年包月带宽这种选项，故没有错误选择带宽的困扰。

带宽大小与费用没有关系。按量付费规则下，是根据服务器的被下载量计算费用，用多少给多少。

**例如**：当前网站所有访问加起来的下载量为：5G，费用大概是：5×0.5 = 2.5元

另外针对静态资源较多的情况，我们建议：

1. 采用CDN
2. 网站图片超过1000张，建议从服务器中分离出去

以上方案简单可靠，降低服务器资源消耗，实现成本较低，效果好。

## 云平台提示漏洞？

云平台不断提醒系统有漏洞或潜在威胁，会不会是镜像默认存在病毒或木马、后门等不安全因素？

**首先，可以肯定的说，绝对不会默认存在病毒或木马、后门**

但需要澄清的是，仅保证**默认**不存在，但是后续出现又是正常的。

软件本身是不断升级迭代发展的，漏洞总是从发现到打补丁的循环中不断成长。镜像中包括：操作系统、中间件、数据库、语言等软件包，没一个软件包都有可能有漏洞。

最新的漏洞就会被发现，云平台就会第一时刻通知到用户，这反而是一件好事。

总而言之，软件的安全是动态系统，软件的本质决定没有人能够在安全上做到“万无一失，疏而不漏”。

另外，从商务角度看，云平台会有监管镜像产品的责任，间接的保障用户的安全：

* 合作选择：保证服务商有丰富的云服务器系统维护和环境配置经验，拥有专业的运维团队；
* 流程控制：要求服务商严格遵循《云平台安全审核标准》，只有通过安全审核的镜像才可以售卖；
* 合规机制：要求服务商须与每一个用户签订《镜像使用许可协议》，对镜像安全向用户作出承诺；

## 需要人工服务？

* 如果您在云平台订阅了我们的收费镜像，您可以享受人工服务，参考：[联系方式](https://support.websoft9.com/zh/contact.html)
* 如果您没有订阅我们的镜像，请到我们的 Github 上的[开源项目](https://github.com/websoft9)中提交 Issue 获取支持。
