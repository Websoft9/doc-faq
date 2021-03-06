# 故障速查

下面列出最常见的故障或设置错误导致的问题。

#### SFTP无法登录？

检查账号和密码是正确，请保证[服务器安全组](/zh/tech-instance.md)的22端口是开启的

#### Windows远程桌面连接失败？

检查账号和密码是正确，请保证[服务器安全组](/zh/tech-instance.md)的3389端口是开启的，下图是排查方法  
![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/aliyun/aliyun-guzhangpaichu.png)

#### 服务器无法重启？

请联系云平台官方修复

#### *http://服务器公网IP* 无法打开软件的初始化界面？

最常见的原因如下：

* 服务器[安全组**80** 端口](/zh/tech-instance.md)没有开启
* 你所安装的镜像不支持此类访问
* 安装的不是目标镜像
* 你的服务器网络故障
* 产品本身的故障导致
* 其他

不管哪种原因，一旦无法访问，请第一时刻联系我们[人工支持](https://support.websoft9.com/zh/contact.html)

#### 已经替换了默认目录的文件，仍然指向Websoft9演示页面？

请清空浏览器缓存 或 换一个浏览器测试

#### 域名解析迟迟没有生效？

解析生效之后，本地访问可能由于缓存问题导致仍然没有生效，请清空浏览器缓存和DNS缓存

#### phpMyAdmin 出现 Error during session...错误？

错误原因：PHP 的 session.save_path 路径目录的权限设置不正确。  
解决方案：打开WinSCP，运行如下命令即可  
~~~
chown -R root:nginx /var/lib/php/session
echo 'chown nginx. -R /var/lib/php' >> /etc/cron.daily/0yum-daily.cron
~~~

#### Nginx出现502错误

Nginx应用服务器出现502错误的原因很多，但是基本都是资源不够造成的。 包括：内存不足，CPU超标，硬盘满了，另外可能也有程序导致php-fpm停止运行。对应的的解决办法：

*   内存和CPU超标，通过重启一下php-fpm 和nginx mysql 三个服务可以临时解决，如果是1核1g的配置且经常出现502错误的话，建议升级
*   硬盘满了的话，会导致MySQL停止服务，需要进行硬盘扩容
*   php-fpm服务停止或者报错也会出现502，需要重启php-fpm

#### 网站速度很慢？

带宽不足以及服务器满负荷运转是最常见的原因，详细分析参考[此处](/zh/#网站访问很慢？)。

#### 连接SFTP，出现Disconnected...publickey

错误原因：选用的是密钥对作为（与root账号密码有区别）登录凭证，而密钥对如果每日有下载到本地是无法在WinSCP等工具中直接使用的

解决方案：设置WinSCP为秘钥对登录 或 云控制台更改登录凭证方式

#### HTTP故障代码有哪些？

如果某项请求发送到您的服务器要求显示您网站上的某个网页（例如用户通过浏览器访问您的网页或 Googlebot 抓取网页时），WEB服务器将会返回 HTTP 状态码响应请求。
此状态代码提供关于请求状态的信息， 告诉 Googlebot 关于您的网站和请求的网页的信息。
一些常见的状态代码:
```
200 服务器成功返回内容
301/2 永久/临时重定向
304 未修改 Not Modified
307 重定向中保留原始数据
404 请求的页面不存在
500 服务器内部错误
503 服务器暂时不可用
```
您也可以访问 [W3C 页面](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) 获取更多HTTP 状态码信息的完整列表。


#### 升级或安装扩展时网络超时？

参考[此处](/zh/#升级或安装扩展时网络超时？)


