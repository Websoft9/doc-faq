# Troubleshooting

The most common faults or problems caused by incorrect settings are listed below.

#### SFTP login failed?

Check you have used the correct username and password, and make sure **TCP:22** of [Security Group of Cloud console](/tech-instance.md) enabled

#### Windows remote connection failed?

Check you have used the correct username and password, and make sure **TCP:3389** of [Security Group of Cloud console](/tech-instance.md) enabled

#### Cloud Server restart failed?

You need to get support from Cloud Platform for this problem.

#### Access URL *http://Cloud Server Internet IP*?

The most common reasons includes:

* **TCP:3389** of [Security Group of Cloud console](/tech-instance.md) disabled
* You application can't access by this URL
* You have deploy an other image not you want
* Your network of Cloud Server failure
* Our image have failure, you can get support from our help desk to fix it
* Other reasons

Regardless of the reason, once you cannot access, please contact us [Help desk](https://support.websoft9.com/contact.html)

#### Always display Websoft9 demo page when replaced the default files in example directory?

Please clear your browser cache or test with another browser

#### Does the domain name resolution take effect?

After the resolution takes effect, local access may still not take effect due to caching issues. Please clear the browser cache and DNS cache

#### 502 error for Nginx?

There are many reasons for the 502 error in the Nginx application server, but they are basically caused by insufficient resources. Including: insufficient memory, excessive CPU, hard disk full, and there may be programs that cause php-fpm to stop running. The corresponding solution:

* The memory and CPU exceed the standard. It can be solved temporarily by restarting the three services of php-fpm and nginx mysql. If it is a 1 core 1g configuration and 502 errors often occur, it is recommended to upgrade
* If the hard disk is full, MySQL will stop service, and hard disk expansion is required
* If the php-fpm service is stopped or an error is reported, 502 will appear, and php-fpm needs to be restarted

#### The website is slow?

Insufficient bandwidth and full server capacity are the most common reasons

#### What are the HTTP fault codes?

```
200 The server successfully returned content
301/2 permanent/temporary redirect
304 Not Modified
307 Keep original data in redirect
404 The requested page does not exist
500 server internal error
503 The server is temporarily unavailable
```
Access the URL [W3C](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) for more details.

