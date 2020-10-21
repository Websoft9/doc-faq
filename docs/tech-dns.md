# Domain Name

The purpose of the Domain Name (DNS) is to point to the website on the server through an easily identifiable paragraph. If there is no domain name, the website can only be accessed through the IP address, which is not easy to remember and identify.

## Configure DNS

If you want to configure DNS for your website, the following steps is for you:  

*   **DNS resolution**: Make your DNS or sub DNS point to a IP address of Server
![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/common/domain-websoft9.png)

*   **DNS binding**: Binding your DNS to a special application directory by modify the **vhost configuration file** when their have more than two websites or applications on your Server.

Following is one sample for LAMP runtime DNS binding:

   ~~~ 
   <VirtualHost *:80>
   ServerName www.mydomain.com
   ServerAlias other.mydomain.com
   DocumentRoot "/data/wwwroot/default/mysite2"
   ErrorLog "/var/log/httpd/www.mydomain.com_error_apache.log"
   CustomLog "/var/log/httpd/www.mydomain.com_apache.log" common
   <Directory "/data/wwwroot/default/mysite1">
   Options Indexes FollowSymlinks
   AllowOverride All
   Require all granted
   </Directory>
   </VirtualHost>
   ~~~

You can modify the item **ServerName, ServerAlias** to implement DNS binding.

> The configuration file mainly includes the corresponding relationship between the Domain Name and the website, that is, which directory a Domain Name should correspond to. If there are multiple websites on the server, it must correspond to multiple configuration files.

## FAQs for DNS

Here are the FAQs you may need:  

#### First-level domain name Second-level domain name?

When you completed one Domain, you owned a first-level Domain Name, e.g abc.com  
When you completed one DNS resolution for your website, e.g www.abc.com, this is a second-level Domain Name  

#### How do domain names and servers associate?

The domain name needs to be resolved to the server through the **A record** to establish an association with the server. After the domain name is resolved to the server IP, the server will use the "domain name configuration file (vhost file)" to determine the mapping relationship between multiple domain names and multiple websites

#### How does the server recognize the level of the domain name?

abc.com and www.abc.com are different Domain Name for Cloud Server.