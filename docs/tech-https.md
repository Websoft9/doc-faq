# SSL/HTTPS

It is easy to configure HTTPS for Websoft9's deployment solution.

## Prepare 

Before you configure HTTPS, make sure that:

* Enable TCP:443 port of your Cloud Console
* Your application can accessed by HTTP
* SSL module of HTTP Server is installed (have installed by default for Websoft9)

## Configure

After the above conditions are specified, you can log in to the server to configure HTTPS. Two solutions are provided here, please choose according to the actual situation:

### Automatic deployment

Just run the one command `sudo certbot` on your instance to start the HTTPS deployment.

```
sudo certbot
```
This solution is based on [Let's Encrypt](https://letsencrypt.org/), and certifications stored in the file: `/etc/letsencrypt/live/`.

![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/common/certbot-ui-websoft9.png)

### Manual deployment

If you have applied for a commercial certificate, complete the HTTPS configuration in just three steps:

1. Upload your certificate, file of the certificate chain and secret key to the directory: */data/cert*.

2. Open the **vhost configuration file** and insert **HTTPS template**
   * For Nginx, the file is  */etc/nginx/conf.d/default.conf*, insert the **HTTPS template** into *server{  }* and modify your certificate path,.
        ``` text
        #-----HTTPS template start------------
        listen 443 ssl; 
        ssl_certificate /data/cert/xxx.crt;
        ssl_certificate_key /data/cert/xxx.key;
        ssl_trusted_certificate /data/cert/chain.pem;
        ssl_session_timeout 5m;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:HIGH:!aNULL:!MD5:!RC4:!DHE;
        ssl_prefer_server_ciphers on;
        #-----HTTPS template end------------
        ```
    * For Apache, the file is */etc/nginx/conf.d/default.conf*, insert the entire **HTTPS template** to it, then modify your certificate path, DocumentRoot.

        ```
        #-----HTTPS template start------------
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
        #-----HTTPS template end------------
        ```
4. All items explanation for you
     
   * ServerName: Primary Domain Name  
   * ServerAlias: Second Domain Name, optional  
   * DocumentRoot: Website root directory, must correct path, e.g. */data/wwwroot/wordpress*
   * Directory: The same with DocumentRoot
   * SSLCertificateFile: SSLCertificate file path
   * SSLCertificateKeyFile: SSLCertificate key file path
   * SSLCertificateChainFile: SSLCertificate key chain file path  

    > `.crt` or `.pem` is the suffix name for SSLCertificate, `.key` is the suffix name for  SSLCertificate key. The incorrect match will cause certificate deployment failure

5. Save file and [restart Nginx or service](/admin-services.md)
   ```
   sudo systemctl restart nginx
   sudo systemctl restart apache
   ```

---

## FAQs for HTTPS

#### Why is the setting successful and it displays "The connection with this website is not completely secure"?

The first option is to make it clear that your HTTPS settings are successful, but because there are static files or external links that contain http access in the website, the browser warns that your website is not completely secure.

#### How to configure HTTP when use CDN?

If you want to use CDN, there have two HTTPS configurations for you:

1. Enable HTTPS on your CDN
2. Enable HTTPS on your Cloud Server

And make sure use the same Certification files on your Cloud Server and CDN.

#### How to enable HTTP redirect to HTTPS?

For Apache, suggest your add the redirect rules in the file **.htacesss** of your application root directory

```
# All redirect
RewriteEngine On
RewriteCond %{SERVER_PORT} 80
RewriteRule ^(.*)$ https://www.yourdomain.com/$1 [R,L]

# Redirect for one Domain
RewriteEngine On
RewriteCond %{HTTP_HOST} ^yourdomain\.com [NC]
RewriteCond %{SERVER_PORT} 80
RewriteRule ^(.*)$ https://www.yourdomain.com/$1 [R,L]

# Redirect for on folder
RewriteEngine On
RewriteCond %{SERVER_PORT} 80
RewriteCond %{REQUEST_URI} folder
RewriteRule ^(.*)$ https://www.yourdomain.com/folder/$1 [R,L]
```

#### Android cannot use HTTPS, but IOS can?

Ensure that **SSLCertificateChainFile** has set the corresponding certificate file

#### Can an IP address apply for a certificate?

No

#### How to deploy HTTPS for Docker applications?

In our solution, it is not recommended to set up HTTPS inside the container, but to configure HTTPS in port forwarding mode through the host's HTTP server (Nginx/Apache, etc.).
