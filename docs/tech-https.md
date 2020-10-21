# SSL/HTTPS

配置HTTPS访问的前置条件：

* 开启服务器安全组的443端口
* 网站通过HTTP可正常访问
* Web服务器已经安装SSL模块（Websoft9提供的所有镜像默认已经安装）

具体以上条件后，便可以登录服务器配置HTTPS。此处提供两种方案，请根据实际情况选择：


## 方案一：自动免费证书配置

Websoft9的镜像默认安装了 [Let's Encrypt](https://letsencrypt.org/) 免费的证书部署软件，只需一条命令就可以启动证书部署.

![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/common/certbot-ui-websoft9.png)

自动部署证书会根据已有的HTTP配置而定，故请确保网站的配置文件中ServerName和ServerAlias中配置有正确的解析后的域名

1. 连接服务器，运行命令 
   ```
   sudo certbot
   ```
2. 根据提示输入对应的内容（下图为范例）

   ![1542853767834](https://libs.websoft9.com/Websoft9/DocsPicture/zh/lamp/certbot-websoft9.png)

   > 第4步可以多选,输入的数字以逗号/空格为分隔

4.  以上步骤操作完成后,certbot将会自动配置好证书,浏览器访问域名检查是否配置成功。生成的网站证书存放目录：`/etc/letsencrypt/live/`

## 方案二：自行上传证书配置

下面以Apache为例，说明上传证书的配置方案：

1.  将可用的证书上传到服务器证书目录：/data/cert（没有cert目录可以自己新建）
2.  编辑虚拟主机配置文件`/etc/httpd/vhost/vhost.conf `，将下面的https配置文件模板拷贝到配置文件中

    ```
    <VirtualHost *:443>
    ServerName  www.mydomain.com
    DocumentRoot "/data/wwwroot/default"
    #ErrorLog "logs/www.mydomain.com-error_log"
    #CustomLog "logs/www.mydomain.com-access_log" common
    <Directory "/data/wwwroot/default">
    Options Indexes FollowSymlinks
    AllowOverride All
    Require all granted
    </Directory>
    SSLEngine on
    SSLCertificateFile  /data/cert/www.mydomain.com.crt
    SSLCertificateKeyFile  /data/cert/www.mydomain.com.key
    SSLCertificateChainFile  /data/cert/www.mydomain.com_chain.crt
    </VirtualHost>
    ```

4.  修改配置文件中相关项，并保存。
     
     ServerName  #主域名，务必修改  
     ServerAlias   #副域名，可选项  
     DocumentRoot #网站路径，务必填写网站实际路径，例如:/data/wwwroot/wordpress  
     Directory #同上  
     SSLCertificateFile #证书，务必填写网站实际路径和名称  
     SSLCertificateKeyFile #证书私钥，务必填写网站实际路径和名称  
     SSLCertificateChainFile #证书链（CA文件），务必填写网站实际路径和名称  

     > 证书的后缀一般是：.crt或者 .pem，私钥的后缀是：.key，填写错误会导致服务无法启动

5.  重启服务

    ```
    systemctl restart httpd
    ```

---

## FAQs for HTTPS

#### 为什么设置成功，显示“与此网站建立的连接并非完全安全”？

首选明确一点即您的HTTPS设置是成功的，只是由于网站中存在包含 http访问的静态文件 或 外部链接等，导致浏览器告警您的网站并非完全安全。

#### 向云平台申请证书的注意事项

*   免费证书只能用于单个域名,例如: buy.example.com,或next.buy.example.com,
*   example.com是通配符域名方式，不能用于申请免费证书
*   申请证书的时候，请先解析好域名，有些证书会绑定域名对应的IP地址，即一旦申请后，IP地址不能更换，否则证书不可用

#### CDN/全站加速开启HTTPS

需要根据云平台参考文档设置。一般来说，此场景下有两个地方需要设置 HTTPS：

1. CDN/全站加速的控制台需设置 HTTPS
2. 服务器中的应用需设置 HTTPS

需要注意的是，两端 HTTPS 必须使用同一套证书。

#### HTTP 自动跳转到 HTTPS 页面

建议在网站根目录下的.htacesss文件中增加redirect规则

```
# 全部跳转
RewriteEngine On
RewriteCond %{SERVER_PORT} 80
RewriteRule ^(.*)$ https://www.yourdomain.com/$1 [R,L]

# 指定域名跳转
RewriteEngine On
RewriteCond %{HTTP_HOST} ^yourdomain\.com [NC]
RewriteCond %{SERVER_PORT} 80
RewriteRule ^(.*)$ https://www.yourdomain.com/$1 [R,L]

# 指定某个目录跳转
RewriteEngine On
RewriteCond %{SERVER_PORT} 80
RewriteCond %{REQUEST_URI} folder
RewriteRule ^(.*)$ https://www.yourdomain.com/folder/$1 [R,L]
```

#### Android 无法使用HTTPS，而IOS可以？

确保SSLCertificateChainFile已设置对应的证书文件

#### IP 地址可以申请证书吗？

不可以，且没有任何意义。

#### Docker 应用如何部署 HTTPS？

我们的方案中，不建议在容器内部设置 HTTPS，而是通过宿主机的 HTTP 服务器（Nginx/Apache等）在端口转发的模式下配置 HTTPS。
