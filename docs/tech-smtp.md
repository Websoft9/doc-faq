# SMTP

Websoft9 Images can be configured to use a third-party SMTP service for outgoing email. These examples may useful for you. If you can't find the your SMTP example, read[ here](https://www.lifewire.com/search?q=smtp) to get more<br />

<a name="a4bf4a01"></a>
## SMTP Server Settings


<a name="SendGrid"></a>
### SendGrid


To configure your application to send email through SendGrid’s SMTP service, use the settings below. Replace USERNAME with your SendGrid account username and PASSWORD with your SendGrid account password.<br />

- SMTP host: smtp.sendgrid.net
- SMTP port: 25 or 587 for unencrypted/TLS email, 465 for SSL-encrypted email
- SMTP username: USERNAME
- SMTP password: PASSWORD

<a name="Gmail"></a>
### Gmail
<br />

- Gmail SMTP server address: **smtp.gmail.com**
- Gmail SMTP username: **Your Gmail address** (e.g. _example@gmail.com_)
- Gmail SMTP password: **Your Gmail password**
- Gmail SMTP port (TLS): **587**
- Gmail SMTP port (SSL): **465**
- Gmail SMTP TLS/SSL required: **yes**

> Remember that in addition to these email server settings, you need to let the email client receive/download mail from your Gmail account too. There's more information on that at the bottom of this page.

[]()
<a name="Outlook.com"></a>
### Outlook.com
<br />

- SMTP Server: smtp-mail.outlook.com
- Username: Your full Outlook.com email address
- Password: Your Outlook.com password
- SMTP Port	587
- SMTP TLS/SSL Encryption Required	Yes

<a name="Hotmail"></a>
### Hotmail

- **Hotmail SMTP Server**: smtp.live.com
- **Hotmail SMTP Username**: Your complete Windows Live Hotmail email address (e.g. _me@hotmail.com_ or _me@live.com_)
- **Hotmail SMTP Password**: Your Windows Live Hotmail password
- **Hotmail SMTP Port**: 587
- **Hotmail SMTP TLS/SSL Required**: yes

<a name="9ec76d42"></a>
### Yahoo Mail

- Yahoo Mail SMTP server address: **smtp.mail.yahoo.com**
- Yahoo Mail SMTP username: Your full [**Yahoo email address**](https://www.lifewire.com/forward-yahoo-mail-to-another-address-1174481) (including **@yahoo.com**)
- Yahoo Mail SMTP password: Your **Yahoo Mail password**
- Yahoo Mail SMTP port: **465 **or** 587**
- Yahoo Mail SMTP TLS/SSL required: **yes**

> These settings work with most desktop, mobile, and web email programs and services. After you set up Yahoo Mail in your preferred email client, the mail and your Yahoo folders appear in both locations: in Yahoo and in your preferred app or web interface, such as Gmail.


<a name="f1091c79"></a>
### QQ Mail

- SMTP host: smtp.qq.com
- SMTP port: 465 or 587for SSL-encrypted email
- SMTP Authentication: must be checked
- SMTP Encryption: must SSL
- SMTP username: email address
- SMTP password: The password is not a mailbox password, but an authorization code that needs to be applied on the SMTP Service page

> The above is for quick reference only. see the [official SMTP for details](https://service.mail.qq.com/cgi-bin/help?subtype=1&&id=28&&no=166)


<a name="cc751c88"></a>
### 163 Mail

- SMTP host: smtp.163.com
- SMTP port: 465 or 994 for SSL-encrypted email
- SMTP Authentication: must be checked
- SMTP Encryption: must SSL
- SMTP username: email address
- SMTP password: The password is not a mailbox password, but an authorization code that needs to be applied on the SMTP Service page

> The above is for quick reference only. see the [official SMTP for details](http://help.163.com/09/1223/14/5R7P6CJ600753VB8.html?servCode=6010376)


<a name="43ff8f5e"></a>
### Aliyun Email

- SMTP host: smtp.mxhichina.com
- SMTP port: 465  for SSL-encrypted email
- SMTP Authentication: must be checked
- SMTP Encryption: must SSL
- SMTP username: email address
- SMTP password: email password

> The above is for quick reference only. see the [official SMTP for details](https://help.aliyun.com/knowledge_detail/36576.html)



<a name="17faeb66"></a>
### iCloud Mail

- Server name:** smtp.mail.me.com**
- SSL required: **Yes**
- Port: **587**
- SMTP authentication required: **Yes**
- Username: Type your full iCloud email address.
- Password: Type an app-specific iCloud Mail password.

<a name="5eb7fdb3"></a>
### Zoho Mail
<br />

- Zoho Mail SMTP server address: **smtp.zoho.com**
- Zoho Mail SMTP port: **465**
- Zoho Mail SMTP TLS/SSL required: **Yes**
- Zoho Mail SMTP user name: **Your** **Zoho Mail address** (example@zoho.com or your email address if you use Zoho Mail with your own domain)
- Zoho Mail SMTP password: **Your** **Zoho Mail password**

<a name="a74039ac"></a>
## Issues with SMTP


SMTP lacks built-in security features. Internet spammers have been enabled to exploit SNMP in the past by generating huge amounts of junk email and having them delivered via open SMTP servers. Protection against spam has improved over the years but are not foolproof. Additionally, SMTP does not prevent spammers from setting (via the MAIL command) fake 'From:' email addresses. 
